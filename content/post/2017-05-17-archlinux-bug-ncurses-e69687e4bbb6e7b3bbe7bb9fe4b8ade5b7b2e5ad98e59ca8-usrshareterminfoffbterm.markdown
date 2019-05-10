---
author: 111qqz
date: 2017-05-17 13:36:18+00:00
draft: false
title: 'archlinux bug ncurses: 文件系统中已存在 /usr/share/terminfo/f/fbterm'
type: post
url: /2017/05/archlinux-bug-ncurses-%e6%96%87%e4%bb%b6%e7%b3%bb%e7%bb%9f%e4%b8%ad%e5%b7%b2%e5%ad%98%e5%9c%a8-usrshareterminfoffbterm/
categories:
- linux
tags:
- archlinux
---

今天滚的时候遇到这个问题...

提示：ncurses: 文件系统中已存在 /usr/share/terminfo/f/fbterm

查了下，由于这bug比较新....没找到什么有用的信息...

于是尝试了一下比较一般的解决冲突的办法：

    
    # pacman -Syuw                           # 用 -Sw 选项仅下载升级所需的包
    # rm /usr/share/terminfo/f/fbterm   # 手动移除冲突的文件
    # pacman -Su                             # 继续升级
    






问题解决。。。


