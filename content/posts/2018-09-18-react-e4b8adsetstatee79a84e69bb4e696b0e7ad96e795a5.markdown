---
author: 111qqz
date: 2018-09-18 13:31:06+00:00
draft: false
title: react 中setState的更新策略
type: post
url: /2018/09/react-%e4%b8%adsetstate%e7%9a%84%e6%9b%b4%e6%96%b0%e7%ad%96%e7%95%a5/
categories:
- 前端
tags:
- react
---

起因是想更新一个array类型的state,结果setState更新之后用console.log() debug 结果，发现结果特别玄学。。。

查了下发现this.setState是个异步操作。。。

参考资料:

[深入理解React 组件状态（State）](https://www.jianshu.com/p/c6257cbef1b1)

[React中setState同步更新策略](https://zhuanlan.zhihu.com/p/24781259)

[https://react.docschina.org/docs/react-component.html](https://react.docschina.org/docs/react-component.html)


