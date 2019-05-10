---
author: 111qqz
date: 2018-02-05 12:54:23+00:00
draft: false
title: C++  Linux下使用popen()执行shell命令
type: post
url: /2018/02/c-linux%e4%b8%8b%e4%bd%bf%e7%94%a8popen%e6%89%a7%e8%a1%8cshell%e5%91%bd%e4%bb%a4/
categories:
- c++
- linux
- 技术科普
tags:
- linux
---

由于需要在Linux平台下，通过cpp获取某个进程所占用的物理内存，得知了这个东西。

感觉还挺厉害的orz..

下面是一段示例代码


    
    #include <iostream>
    #include <stdio.h>
    using namespace std;
    int main() {
        FILE *in;
        char buff[512];
        if(!(in = popen("ps -C codeblocks -o %cpu,%mem | tail -n 2", "r"))){
            return 1;
        }
        while(fgets(buff, sizeof(buff), in)!=NULL){
            cout << buff;
        }
        pclose(in);
        return 0;
    } 
    




