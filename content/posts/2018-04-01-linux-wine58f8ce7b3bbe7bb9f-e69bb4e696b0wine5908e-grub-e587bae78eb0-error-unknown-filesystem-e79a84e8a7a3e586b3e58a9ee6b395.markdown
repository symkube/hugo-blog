---
author: 111qqz
date: 2018-04-01 06:28:30+00:00
draft: false
title: 'linux/win双系统 更新win后 grub 出现 Error: unknown filesystem 的解决办法'
type: post
url: /2018/04/linux-win%e5%8f%8c%e7%b3%bb%e7%bb%9f-%e6%9b%b4%e6%96%b0win%e5%90%8e-grub-%e5%87%ba%e7%8e%b0-error-unknown-filesystem-%e7%9a%84%e8%a7%a3%e5%86%b3%e5%8a%9e%e6%b3%95/
categories:
- 技术科普
tags:
- grub
---

windows自己更新把grub更新挂了....

更新的时候要重启几次,重启一次挂一次...

讲真,windows(或者说win10?) 是我见过的最辣鸡的OS了...  自己把自己弄挂这事不是一两次了.

下面说修复办法:

先ls,得到一堆诸如(hd0,gpt7) 这种

然后选设X=第一个(x,y)形式的输出

之后


    
    <code>set root=X
    set prefix=X/boot/grub
    insmod normal
    normal
    </code>



然后记得要进入linux分区.....
执行:
sudo update-grub
sudo grub-install /dev/sda



# 总结:**珍爱生命,远离辣鸡windows!!!!!**





# **珍爱生命,远离辣鸡windows!!!!!**





# **珍爱生命,远离辣鸡windows!!!!!**




