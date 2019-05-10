---
author: 111qqz
date: 2018-02-12 07:19:45+00:00
draft: false
title: CMake Error at gpuxgboost_generated_updater_gpu_hist_experimental.cu.obj.Release.cmake:282  的解决办法
type: post
url: /2018/02/cmake-error-at-gpuxgboost_generated_updater_gpu_hist_experimental-cu-obj-release-cmake282-%e7%9a%84%e8%a7%a3%e5%86%b3%e5%8a%9e%e6%b3%95/
categories:
- deep-learning
tags:
- cuda
- thrust
---

请教了同事...果然是身经百战见得多啊

直接告诉我cuda 8.0.27 对应版本的thrust有bug.

解决办法是从 thrust 的github搞一份最新的下来，并覆盖掉/usr/local/cuda/include/thrust/






