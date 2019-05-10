---
author: 111qqz
date: 2017-08-24 07:53:12+00:00
draft: false
title: tensorflow 术语总结（不断更新）
type: post
url: /2017/08/tensorflow-%e6%9c%af%e8%af%ad%e6%80%bb%e7%bb%93%ef%bc%88%e4%b8%8d%e6%96%ad%e6%9b%b4%e6%96%b0%ef%bc%89/
categories:
- computer vision
tags:
- tensorflow
---

epoch：一个数据集完整得过一遍叫一个epoch,比如100w个数据，batch_size=100,那么训练1W个batch才是一个epoch

batch_size:由于数据一个一个训练效率太低，所以将若干数据合在一起，称为一个batch,一起训练以提高效率。一个batch中数据的个数称为batch_size
