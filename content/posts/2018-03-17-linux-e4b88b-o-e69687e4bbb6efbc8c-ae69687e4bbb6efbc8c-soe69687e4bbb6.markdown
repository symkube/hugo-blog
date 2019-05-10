---
author: 111qqz
date: 2018-03-17 12:56:33+00:00
draft: false
title: linux 下 .o 文件， .a文件，.so文件
type: post
url: /2018/03/linux-%e4%b8%8b-o-%e6%96%87%e4%bb%b6%ef%bc%8c-a%e6%96%87%e4%bb%b6%ef%bc%8c-so%e6%96%87%e4%bb%b6/
categories:
- c++
tags:
- linux
---

发现我对工程一无所知QAQ

参考资料：

[LibraryArchives-StaticAndDynamic](http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html)

简单得说就是：A  .a file is a static library, while a .so file is a shared object (dynamic) library similar to a DLL on Windows.

至于.o文件，其实就相当于win下的obj文件。至于win下的obj文件，其实就是因为编译没办法一次编译所有文件得到.exe文件，所以生成了中间的文件，就是.obj文件。

生成静态库还是动态库是开发者可以选择的，不过需要遵循一些原则。

静态库的好处是，把程序给用户之后，不需要再给额外的库就可以直接运行了。

但是程序会比较臃肿。






