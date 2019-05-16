---
author: 111qqz
date: 2018-02-11 08:06:14+00:00
draft: false
title: 'CUDA 7.5: 用指令级性能分析精确找到性能问题'
type: post
url: /2018/02/cuda-7-5-pinpoint-performance-problems-instruction-level-profiling/
categories:
- 优化
tags:
- cuda
---

原文：

[CUDA 7.5: Pinpoint Performance Problems with Instruction-Level Profiling](https://devblogs.nvidia.com/cuda-7-5-pinpoint-performance-problems-instruction-level-profiling/)



主要是介绍了CUDA 7.5 以上的版本的 NVIDIA Visual Profiler 加入的新特性

可以细粒度到指令级，分析出性能的瓶颈（在这之前，只能分析到kernel级别）

顺便了解了一下[nvidia-visual-profiler](http://docs.nvidia.com/cuda/profiler-users-guide/index.html)

原理大概是用PC（程序计数器）采样目前活跃的warp,然后得到这些warp的PC和状态，以此来得到更细粒度的性能分析。



<blockquote>Instruction-level profiling in CUDA 7.5 uses program counter (PC) sampling with a per-streaming-multiprocessor (SM) fixed-frequency sampler. At each sample period, the collector picks an active warp from the SM and captures the warp’s PC and warp state. Warp selection is performed round-robin across all active warps on the SM.</blockquote>



文中还给出了分析完性能瓶颈之后做出的相应优化。

下面是对一段存在内存依赖延迟（？Memory Dependency Stalls ）问题的代码给出优化的过程。


    
    float row[7]
    //Initialize array row
    int shift = 0;
    __shared__ float smem[CTA_SIZE];
    for (int i = 0; i < 6; ++i)        // rows
    {
        #pragma unroll
        for (int j = i; j < 7; ++j)    // cols + b
        {
            __syncthreads ();
            smem[tid] = row[i] * row[j];
            __syncthreads ();
    
            reduce(smem);
    
            if (tid == 0)
                gbuf.ptr (shift++)[blockIdx.x + gridDim.x * blockIdx.y] 
                    = smem[0];
        }
    }



我们注意到代码第一行定义了一个size为7的float类型的数组，性能分析表明这一行涉及了 LDL(“load local”)  指令,是性能的瓶颈之一。

为什么？

因为NVIDIA 的GPU 没有下标 寄存器文件，所以如果一个数组被以动态的下标访问，编译器不得不为这个数组分配local memory.

在Maxwell 架构中，local memory 没有被加入在L1 缓存中,因此访问内存会有很大的延迟。

所以为了优化这部分，就把数组拆分成相同个数的单独的变量。

然后由于没有定义成数组，因此也需要把循环展开。

优化后的代码如下：


    
    float row0, row1, row2, row3, row4, row5, row6; 
    //Initialize all elements
    #define UNROLL_REDUCE(val, buf)                                     \
        do {                                                            \
            smem[tid] = val;                                            \
                __syncthreads();                                        \
                reduce(smem);                                           \
                if (tid == 0)                                           \
                    buf.ptr (shift++)[blockIdx.x + gridDim.x * blockIdx.y] \
                        = smem[0]; \
        } while(0)
    
    UNROLL_REDUCE(row0*row0, gbuf);
    UNROLL_REDUCE(row0*row1, gbuf);
    UNROLL_REDUCE(row0*row2, gbuf);
    UNROLL_REDUCE(row0*row3, gbuf);
    UNROLL_REDUCE(row0*row4, gbuf);
















