---
author: 111qqz
date: 2018-02-09 07:11:54+00:00
draft: false
title: cuda 学习笔记 术语篇
type: post
url: /2018/02/cuda-%e5%ad%a6%e4%b9%a0%e7%ac%94%e8%ae%b0-%e6%9c%af%e8%af%ad%e7%af%87/
categories:
- computer vision
- deep-learning
tags:
- cuda
---

最近在学习cuda,遇到的新词汇有点多,所以开一篇记录一下.

所记录的不一定和cuda有关,只是在学习cuda中遇到的陌生概念.




      * **SIMD(Single Instruction Multiple Data)  单指令流多数据流  是一种采用一个[控制器](https://zh.wikipedia.org/wiki/%E6%8E%A7%E5%88%B6%E5%99%A8)来控制多个[处理器](https://zh.wikipedia.org/wiki/%E5%A4%84%E7%90%86%E5%99%A8)，同时对一组数据（又称“[数据向量](https://zh.wikipedia.org/w/index.php?title=%E6%95%B0%E6%8D%AE%E5%90%91%E9%87%8F&action=edit&redlink=1)”）中的每一个分别执行相同的操作从而实现空间上的[并行](https://zh.wikipedia.org/wiki/%E5%B9%B6%E8%A1%8C)性的技术。[图形处理器](https://zh.wikipedia.org/wiki/%E5%9C%96%E5%BD%A2%E8%99%95%E7%90%86%E5%99%A8)（GPU）拥有强大的并发处理能力和可编程流水线，面对单指令流多数据流时，运算能力远超传统CPU。[OpenCL](https://zh.wikipedia.org/wiki/OpenCL)和[CUDA](https://zh.wikipedia.org/wiki/CUDA)分别是目前最广泛使用的开源和专利[通用图形处理器](https://zh.wikipedia.org/wiki/%E9%80%9A%E7%94%A8%E5%9C%96%E5%BD%A2%E8%99%95%E7%90%86%E5%99%A8)（GPGPU）运算语言。**
      * 


SAXPY （**Scalar Alpha X Plus Y**）operation, 其实就是![{\displaystyle \mathbf {y} =\alpha \mathbf {x} +\mathbf {y} ,\,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/92099e1e67371aa793923907abaf4b309667a747)
  其中![\alpha ](https://wikimedia.org/api/rest_v1/media/math/render/svg/b79333175c8b3f0840bfb4ec41b8072c83ea88d3)
是[标量](https://zh.wikipedia.org/wiki/%E6%A0%87%E9%87%8F)，![\mathbf {x} ](https://wikimedia.org/api/rest_v1/media/math/render/svg/32adf004df5eb0a8c7fd8c0b6b7405183c5a5ef2)
和![\mathbf {y} ](https://wikimedia.org/api/rest_v1/media/math/render/svg/bb25a040b592282dc2a254c3117e792c3c81161f)
是[矢量](https://zh.wikipedia.org/wiki/%E7%9F%A2%E9%87%8F)。




