---
author: 111qqz
date: 2017-08-11 08:59:10+00:00
draft: false
title: 分布式tensorflow 设备分配 学习笔记
type: post
url: /2017/08/%e5%88%86%e5%b8%83%e5%bc%8ftensorflow-%e8%ae%be%e5%a4%87%e5%88%86%e9%85%8d-%e5%ad%a6%e4%b9%a0%e7%ac%94%e8%ae%b0tf-train-replica_device_setter-and-more/
categories:
- computer vision
tags:
- tensorflow
- 分布式
---





[replica_device_setter_TF官网文档](https://www.tensorflow.org/api_docs/python/tf/train/replica_device_setter)

由于看到这个函数很是激动。。。感觉这个东西也是蛮重要的。。之前完全手动分配累死辣。。。

所以单独写一篇，主要是翻译replica_device_setter的文档，之后和分布式 tensorflow 设备分配相关的内容也会放在这里



# tf.train.replica_device_setter





## 函数原型




    
    replica_device_setter(
        ps_tasks=0,
        ps_device='/job:ps',
        worker_device='/job:worker',
        merge_devices=True,
        cluster=None,
        ps_ops=None,
        ps_strategy=None
    )





## 用法



device functions是用在_tf.device(device_function) 中_来自动向op objects 分配设备的。

设备的作用域优先级从内向外（类似变量的作用域

目前可以设置的域的关键字有（job, task, cpu/gpu）

如果cluster没有被定义，并且ps_tasks为0，那么该函数返回一个no-op（no-op应该就是operation界的null类型）

默认情况下，只有变量的op会被放在ps上，放置策略是在 所有ps tasks上用 [Round-robin](https://en.wikipedia.org/wiki/Round-robin_scheduling)

该策略也可以自定义，参考[GreedyLoadBalancingStrategy](https://www.tensorflow.org/api_docs/python/tf/contrib/training/GreedyLoadBalancingStrategy)



## 例子




    
    # To build a cluster with two ps jobs on hosts ps0 and ps1, and 3 worker
    # jobs on hosts worker0, worker1 and worker2.
    cluster_spec = {
        "ps": ["ps0:2222", "ps1:2222"],
        "worker": ["worker0:2222", "worker1:2222", "worker2:2222"]}
    with tf.device(tf.train.replica_device_setter(cluster=cluster_spec)):
      # Build your graph
      v1 = tf.Variable(...)  # assigned to /job:ps/task:0
      v2 = tf.Variable(...)  # assigned to /job:ps/task:1
      v3 = tf.Variable(...)  # assigned to /job:ps/task:0
    # Run compute





## 参数






      * **`ps_tasks`**: Number of tasks in the `ps` job. Ignored if `cluster` is provided.
      * **`ps_device`**: String. Device of the `ps` job. If empty no `ps` job is used. Defaults to `ps`.
      * **`worker_device`**: String. Device of the `worker` job. If empty no `worker` job is used.
      * **`merge_devices`**: `Boolean`. If `True`, merges or only sets a device if the device constraint is completely unset. merges device specification rather than overriding them.
      * **`cluster`**: `ClusterDef` proto or `ClusterSpec`.
      * **`ps_ops`**: List of strings representing `Operation` types that need to be placed on `ps` devices. If `None`, defaults to `["Variable"]`.
      * **`ps_strategy`**: A callable invoked for every ps `Operation` (i.e. matched by `ps_ops`), that takes the `Operation` and returns the ps task index to use. If `None`, defaults to a round-robin strategy across all `ps` devices.










# 其他



allow_soft_placement:session的一个属性，可以用来防止指定的设备不存在而导致无法运行的情况。设置为true会自动选择存在的设备。




