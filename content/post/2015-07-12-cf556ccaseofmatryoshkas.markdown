---
author: 111qqz
date: 2015-07-12 03:39:00+00:00
draft: false
title: cf 556C Case of Matryoshkas
type: post
url: /2015/07/cf556ccaseofmatryoshkas/
categories:
- ACM
---

http://codeforces.com/contest/556/problem/C




果然一晚上不睡觉会导致读错题么...




需要注意的是 如果有一个是 1 2 4 6  那么 1,2是不必拆开的....




然后我们发现,只有以1为开始且连续的套娃不必拆开....




可以先假设所有都需要拆开,那么一共需要 2*n-k-1次




然后如果有以1为开始连续的,拆的时候少拆一次,装的时候少装一次,所以ans=ans-2




但是需要注意的是....如果只有一个1,比如1 3 5  也算成了长度为1的以1开始连续的,但是这并没有什么卵用....所以最后答案记得ans+2






    
    <span style="color: #008000;">/*</span><span style="color: #008000;">************************************************************************
        > File Name: code/cf/556C.cpp
        > Author: 111qqz
        > Email: rkz2013@126.com 
        > Created Time: 2015年07月12日 星期日 10时24分54秒
     ***********************************************************************</span><span style="color: #008000;">*/</span><span style="color: #000000;">
    
    #include</span><iostream><span style="color: #000000;">
    #include</span><iomanip><span style="color: #000000;">
    #include</span><cstdio><span style="color: #000000;">
    #include</span><algorithm><span style="color: #000000;">
    #include</span><cmath><span style="color: #000000;">
    #include</span><cstring><span style="color: #000000;">
    #include</span><<span style="color: #0000ff;">string</span>><span style="color: #000000;">
    #include</span><map><span style="color: #000000;">
    #include</span><<span style="color: #0000ff;">set</span>><span style="color: #000000;">
    #include</span><queue><span style="color: #000000;">
    #include</span><vector><span style="color: #000000;">
    #include</span><stack>
    <span style="color: #0000ff;">using</span> <span style="color: #0000ff;">namespace</span><span style="color: #000000;"> std;
    typedef </span><span style="color: #0000ff;">long</span> <span style="color: #0000ff;">long</span><span style="color: #000000;"> LL;
    typedef unsigned </span><span style="color: #0000ff;">long</span> <span style="color: #0000ff;">long</span><span style="color: #000000;"> ULL;
    </span><span style="color: #0000ff;">const</span> <span style="color: #0000ff;">int</span> N=1E5+<span style="color: #800080;">7</span><span style="color: #000000;">;
    </span><span style="color: #0000ff;">int</span><span style="color: #000000;"> a[N],m[N];
    LL n,k,ans;
    </span><span style="color: #0000ff;">int</span><span style="color: #000000;"> main()
    {
        cin</span>>>n>><span style="color: #000000;">k;
        ans </span>= <span style="color: #800080;">2</span>*n-k+<span style="color: #800080;">1</span><span style="color: #000000;">;
        </span><span style="color: #0000ff;">for</span> (<span style="color: #0000ff;">int</span> i = <span style="color: #800080;">0</span> ; i < k ; i++<span style="color: #000000;"> )
        {
          scanf(</span><span style="color: #800000;">"</span><span style="color: #800000;">%d</span><span style="color: #800000;">"</span>,&<span style="color: #000000;">m[i]);
          </span><span style="color: #0000ff;">for</span> (<span style="color: #0000ff;">int</span> j = <span style="color: #800080;">0</span> ; j < m[i];j++<span style="color: #000000;">)
          {
            scanf(</span><span style="color: #800000;">"</span><span style="color: #800000;">%d</span><span style="color: #800000;">"</span>,&<span style="color: #000000;">a[j]);
            </span><span style="color: #0000ff;">if</span> (a[j]==j+<span style="color: #800080;">1</span><span style="color: #000000;">)
                ans </span>= ans -<span style="color: #800080;">2</span><span style="color: #000000;">;
    
          }
        }
        cout</span><<ans<<<span style="color: #000000;">endl;
        </span><span style="color: #0000ff;">return</span> <span style="color: #800080;">0</span><span style="color: #000000;">;
    }</span>






