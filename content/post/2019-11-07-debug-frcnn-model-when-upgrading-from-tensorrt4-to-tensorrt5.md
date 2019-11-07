---
title: "faster rcnn 模型 tensorrt4与tensorrt5 结果不一致 踩坑记录"
date: 2019-11-07T23:40:39+08:00
draft: false

type: post
url: /2018/02/debug-Frcnn-Model-When-Upgrading-From-Tensorrt4-to-Tensorrt5/
categories:
- deep-learning
tags:
- faster-rcnn
---

最近有同事report给我们,用同一个模型转换工具,转同一个faster rcnn 模型, 同样的sdk代码,在有些显卡上结果正常,但是再比较新的显卡上(比如Titan V)上 结果完全不正确.

听说之后我的内心其实是 **喵喵喵喵喵?**的

先在模型转换工具中infer了一下,发现...结果竟然真的不一样!

于是又开始了debug faster rcnn 的旅程(奇怪..我为什么要说又)


一份典型的faster rcnn 的

[prototxt](https://github.com/rbgirshick/py-faster-rcnn/blob/master/models/coco/VGG16/faster_rcnn_end2end/test.prototxt)

按照经验,我们先对照了ROIS,来判断RPN 是否存在问题

惊讶地发现,竟然是没有问题的...

那看一下模型的输出 cls_score 和 bbox_pred好了
发现cls_score 完全对不上,bbox_pred 倒是没问题...
这和之前遇到的情况不太一样啊... 从proposal layer 到 最后...
全都是些很常见的layer... 哪里会有问题呢...

最终发现有问题的layer 是softmax!

cls_score 的维度应该为 N\*K\*C\*H\*W





