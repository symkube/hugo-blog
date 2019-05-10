---
author: 111qqz
date: 2019-02-23 14:28:01+00:00
draft: false
title: manjaro /archlinux 下 steam 文明5/6(civilization V/VI)的运行方法
type: post
url: /2019/02/manjaro-archlinux-%e4%b8%8b-steam-%e6%96%87%e6%98%8e5-6civilization-v-vi%e7%9a%84%e8%bf%90%e8%a1%8c%e6%96%b9%e6%b3%95/
categories:
- 随笔杂谈
tags:
- steam
- 文明
---

系统版本为Manjaro 18.0.3 Illyria

运行文明5比较容易，只需要设置启动选项为:

LD_PRELOAD=/usr/lib32/libopenal.so.1 %command%



文明6运行会报错 undefined symbol: FT_Done_MM_Var

解决办法是 在终端中用如下办法运行steam:

LD_PRELOAD=/usr/lib/libfreetype.so steam

[参考链接](https://forum.manjaro.org/t/steam-recently-civ-vi-stops-to-launch/68244/3)


