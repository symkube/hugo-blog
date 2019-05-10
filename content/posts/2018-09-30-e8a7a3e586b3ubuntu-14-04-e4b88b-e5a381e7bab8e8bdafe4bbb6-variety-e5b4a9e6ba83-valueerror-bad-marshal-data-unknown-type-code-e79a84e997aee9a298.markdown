---
author: 111qqz
date: 2018-09-30 08:59:31+00:00
draft: false
title: '解决ubuntu 14.04 下 壁纸软件 variety 崩溃 ValueError: bad marshal data (unknown type
  code) 的问题'
type: post
url: /2018/09/%e8%a7%a3%e5%86%b3ubuntu-14-04-%e4%b8%8b-%e5%a3%81%e7%ba%b8%e8%bd%af%e4%bb%b6-variety-%e5%b4%a9%e6%ba%83-valueerror-bad-marshal-data-unknown-type-code-%e7%9a%84%e9%97%ae%e9%a2%98/
categories:
- linux
tags:
- linux
---

系统为ubuntu 14.04

迫于特别想定时换壁纸，查了下解决方案。

发现只要删除掉/usr目录下所有的'.pyc'文件就可以

命令为:sudo find /usr -name '*.pyc' -delete
