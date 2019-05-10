---
author: 111qqz
date: 2015-04-14 20:27:00+00:00
draft: false
title: cf 535B Tavas and SaDDas
type: post
url: /2015/04/cf535btavasandsaddas/
categories:
- ACM
---
















B. Tavas and SaDDas







time limit per test


1 second







memory limit per test


256 megabytes







input


standard input







output


standard output










Once again Tavas started eating coffee mix without water! Keione told him that it smells awful, but he didn't stop doing that. That's why Keione told his smart friend, SaDDas to punish him! SaDDas took Tavas' headphones and told him: "If you solve the following problem, I'll return it to you."


![](https://111qqz.com/wp-content/uploads/2015/11/5a1e4a3bffa5e062b65eaef4c4b3351901d198c4.png)



The problem is:




You are given a lucky number _n_. Lucky numbers are the positive integers whose decimal representations contain only the lucky digits 4 and 7. For example, numbers 47, 744, 4 are lucky and 5, 17, 467 are not.




If we sort all lucky numbers in increasing order, what's the 1-based index of _n_?




Tavas is not as smart as SaDDas, so he asked you to do him a favor and solve this problem so he can have his headphones back.










Input




The first and only line of input contains a lucky number _n_ (1 ≤ _n_ ≤ 109).










Output




Print the index of _n_ among all lucky numbers.










Sample test(s)










input



    
    4










output



    
    1










input



    
    7










output



    
    2










input



    
    77










output



    
    6










题意是只由数字4和数字7组成的数称为lucky number。。。给出一个lucky number 问是第几个....




看数据，，10^9.。。打表打法好啊！ 大概10S吧。。。出结果...









    
    #include <iostream><span style="color: #000000;">
    #include </span><algorithm><span style="color: #000000;">
    #include </span><cstring><span style="color: #000000;">
    #include </span><cstdio><span style="color: #000000;">
    #include </span><cmath>
    <span style="color: #0000ff;">using</span> <span style="color: #0000ff;">namespace</span><span style="color: #000000;"> std;
    typedef </span><span style="color: #0000ff;">long</span> <span style="color: #0000ff;">long</span><span style="color: #000000;"> LL;
    </span><span style="color: #0000ff;">const</span> <span style="color: #0000ff;">int</span> N=1E9+<span style="color: #800080;">9</span><span style="color: #000000;">;
    </span><span style="color: #0000ff;">bool</span><span style="color: #000000;"> flag;
    </span><span style="color: #0000ff;">int</span> n,k,a[<span style="color: #800080;">999999</span>]={<span style="color: #800080;">4</span>,<span style="color: #800080;">7</span>,<span style="color: #800080;">44</span>,<span style="color: #800080;">47</span>,<span style="color: #800080;">74</span>,<span style="color: #800080;">77</span>,<span style="color: #800080;">444</span>,<span style="color: #800080;">447</span>,<span style="color: #800080;">474</span>,<span style="color: #800080;">477</span>,<span style="color: #800080;">744</span>,<span style="color: #800080;">747</span>,<span style="color: #800080;">774</span>,<span style="color: #800080;">777</span>,<span style="color: #800080;">4444</span>,<span style="color: #800080;">4447</span>,<span style="color: #800080;">4474</span>,<span style="color: #800080;">4477</span>,<span style="color: #800080;">4744</span>,<span style="color: #800080;">4747</span>,<span style="color: #800080;">4774</span>,<span style="color: #800080;">4777</span>,<span style="color: #800080;">7444</span>,<span style="color: #800080;">7447</span>,<span style="color: #800080;">7474</span>,<span style="color: #800080;">7477</span>,<span style="color: #800080;">7744</span>,<span style="color: #800080;">7747</span>,<span style="color: #800080;">7774</span>,<span style="color: #800080;">7777</span>,<span style="color: #800080;">44444</span>,<span style="color: #800080;">44447</span>,<span style="color: #800080;">44474</span>,<span style="color: #800080;">44477</span>,<span style="color: #800080;">44744</span>,<span style="color: #800080;">44747</span>,<span style="color: #800080;">44774</span>,<span style="color: #800080;">44777</span>,<span style="color: #800080;">47444</span>,<span style="color: #800080;">47447</span>,<span style="color: #800080;">47474</span>,<span style="color: #800080;">47477</span>,<span style="color: #800080;">47744</span>,<span style="color: #800080;">47747</span>,<span style="color: #800080;">47774</span>,<span style="color: #800080;">47777</span>,<span style="color: #800080;">74444</span>,<span style="color: #800080;">74447</span>,<span style="color: #800080;">74474</span>,<span style="color: #800080;">74477</span>,<span style="color: #800080;">74744</span>,<span style="color: #800080;">74747</span>,<span style="color: #800080;">74774</span>,<span style="color: #800080;">74777</span>,<span style="color: #800080;">77444</span>,<span style="color: #800080;">77447</span>,<span style="color: #800080;">77474</span>,<span style="color: #800080;">77477</span>,<span style="color: #800080;">77744</span>,<span style="color: #800080;">77747</span>,<span style="color: #800080;">77774</span>,<span style="color: #800080;">77777</span>,<span style="color: #800080;">444444</span>,<span style="color: #800080;">444447</span>,<span style="color: #800080;">444474</span>,<span style="color: #800080;">444477</span>,<span style="color: #800080;">444744</span>,<span style="color: #800080;">444747</span>,<span style="color: #800080;">444774</span>,<span style="color: #800080;">444777</span>,<span style="color: #800080;">447444</span>,<span style="color: #800080;">447447</span>,<span style="color: #800080;">447474</span>,<span style="color: #800080;">447477</span>,<span style="color: #800080;">447744</span>,<span style="color: #800080;">447747</span>,<span style="color: #800080;">447774</span>,<span style="color: #800080;">447777</span>,<span style="color: #800080;">474444</span>,<span style="color: #800080;">474447</span>,<span style="color: #800080;">474474</span>,<span style="color: #800080;">474477</span>,<span style="color: #800080;">474744</span>,<span style="color: #800080;">474747</span>,<span style="color: #800080;">474774</span>,<span style="color: #800080;">474777</span>,<span style="color: #800080;">477444</span>,<span style="color: #800080;">477447</span>,<span style="color: #800080;">477474</span>,<span style="color: #800080;">477477</span>,<span style="color: #800080;">477744</span>,<span style="color: #800080;">477747</span>,<span style="color: #800080;">477774</span>,<span style="color: #800080;">477777</span>,<span style="color: #800080;">744444</span>,<span style="color: #800080;">744447</span>,<span style="color: #800080;">744474</span>,<span style="color: #800080;">744477</span>,<span style="color: #800080;">744744</span>,<span style="color: #800080;">744747</span>,<span style="color: #800080;">744774</span>,<span style="color: #800080;">744777</span>,<span style="color: #800080;">747444</span>,<span style="color: #800080;">747447</span>,<span style="color: #800080;">747474</span>,<span style="color: #800080;">747477</span>,<span style="color: #800080;">747744</span>,<span style="color: #800080;">747747</span>,<span style="color: #800080;">747774</span>,<span style="color: #800080;">747777</span>,<span style="color: #800080;">774444</span>,<span style="color: #800080;">774447</span>,<span style="color: #800080;">774474</span>,<span style="color: #800080;">774477</span>,<span style="color: #800080;">774744</span>,<span style="color: #800080;">774747</span>,<span style="color: #800080;">774774</span>,<span style="color: #800080;">774777</span>,<span style="color: #800080;">777444</span>,<span style="color: #800080;">777447</span>,<span style="color: #800080;">777474</span>,<span style="color: #800080;">777477</span>,<span style="color: #800080;">777744</span>,<span style="color: #800080;">777747</span>,<span style="color: #800080;">777774</span>,<span style="color: #800080;">777777</span>,<span style="color: #800080;">4444444</span>,<span style="color: #800080;">4444447</span>,<span style="color: #800080;">4444474</span>,<span style="color: #800080;">4444477</span>,<span style="color: #800080;">4444744</span>,<span style="color: #800080;">4444747</span>,<span style="color: #800080;">4444774</span>,<span style="color: #800080;">4444777</span>,<span style="color: #800080;">4447444</span>,<span style="color: #800080;">4447447</span>,<span style="color: #800080;">4447474</span>,<span style="color: #800080;">4447477</span>,<span style="color: #800080;">4447744</span>,<span style="color: #800080;">4447747</span>,<span style="color: #800080;">4447774</span>,<span style="color: #800080;">4447777</span>,<span style="color: #800080;">4474444</span>,<span style="color: #800080;">4474447</span>,<span style="color: #800080;">4474474</span>,<span style="color: #800080;">4474477</span>,<span style="color: #800080;">4474744</span>,<span style="color: #800080;">4474747</span>,<span style="color: #800080;">4474774</span>,<span style="color: #800080;">4474777</span>,<span style="color: #800080;">4477444</span>,<span style="color: #800080;">4477447</span>,<span style="color: #800080;">4477474</span>,<span style="color: #800080;">4477477</span>,<span style="color: #800080;">4477744</span>,<span style="color: #800080;">4477747</span>,<span style="color: #800080;">4477774</span>,<span style="color: #800080;">4477777</span>,<span style="color: #800080;">4744444</span>,<span style="color: #800080;">4744447</span>,<span style="color: #800080;">4744474</span>,<span style="color: #800080;">4744477</span>,<span style="color: #800080;">4744744</span>,<span style="color: #800080;">4744747</span>,<span style="color: #800080;">4744774</span>,<span style="color: #800080;">4744777</span>,<span style="color: #800080;">4747444</span>,<span style="color: #800080;">4747447</span>,<span style="color: #800080;">4747474</span>,<span style="color: #800080;">4747477</span>,<span style="color: #800080;">4747744</span>,<span style="color: #800080;">4747747</span>,<span style="color: #800080;">4747774</span>,<span style="color: #800080;">4747777</span>,<span style="color: #800080;">4774444</span>,<span style="color: #800080;">4774447</span>,<span style="color: #800080;">4774474</span>,<span style="color: #800080;">4774477</span>,<span style="color: #800080;">4774744</span>,<span style="color: #800080;">4774747</span>,<span style="color: #800080;">4774774</span>,<span style="color: #800080;">4774777</span>,<span style="color: #800080;">4777444</span>,<span style="color: #800080;">4777447</span>,<span style="color: #800080;">4777474</span>,<span style="color: #800080;">4777477</span>,<span style="color: #800080;">4777744</span>,<span style="color: #800080;">4777747</span>,<span style="color: #800080;">4777774</span>,<span style="color: #800080;">4777777</span>,<span style="color: #800080;">7444444</span>,<span style="color: #800080;">7444447</span>,<span style="color: #800080;">7444474</span>,<span style="color: #800080;">7444477</span>,<span style="color: #800080;">7444744</span>,<span style="color: #800080;">7444747</span>,<span style="color: #800080;">7444774</span>,<span style="color: #800080;">7444777</span>,<span style="color: #800080;">7447444</span>,<span style="color: #800080;">7447447</span>,<span style="color: #800080;">7447474</span>,<span style="color: #800080;">7447477</span>,<span style="color: #800080;">7447744</span>,<span style="color: #800080;">7447747</span>,<span style="color: #800080;">7447774</span>,<span style="color: #800080;">7447777</span>,<span style="color: #800080;">7474444</span>,<span style="color: #800080;">7474447</span>,<span style="color: #800080;">7474474</span>,<span style="color: #800080;">7474477</span>,<span style="color: #800080;">7474744</span>,<span style="color: #800080;">7474747</span>,<span style="color: #800080;">7474774</span>,<span style="color: #800080;">7474777</span>,<span style="color: #800080;">7477444</span>,<span style="color: #800080;">7477447</span>,<span style="color: #800080;">7477474</span>,<span style="color: #800080;">7477477</span>,<span style="color: #800080;">7477744</span>,<span style="color: #800080;">7477747</span>,<span style="color: #800080;">7477774</span>,<span style="color: #800080;">7477777</span>,<span style="color: #800080;">7744444</span>,<span style="color: #800080;">7744447</span>,<span style="color: #800080;">7744474</span>,<span style="color: #800080;">7744477</span>,<span style="color: #800080;">7744744</span>,<span style="color: #800080;">7744747</span>,<span style="color: #800080;">7744774</span>,<span style="color: #800080;">7744777</span>,<span style="color: #800080;">7747444</span>,<span style="color: #800080;">7747447</span>,<span style="color: #800080;">7747474</span>,<span style="color: #800080;">7747477</span>,<span style="color: #800080;">7747744</span>,<span style="color: #800080;">7747747</span>,<span style="color: #800080;">7747774</span>,<span style="color: #800080;">7747777</span>,<span style="color: #800080;">7774444</span>,<span style="color: #800080;">7774447</span>,<span style="color: #800080;">7774474</span>,<span style="color: #800080;">7774477</span>,<span style="color: #800080;">7774744</span>,<span style="color: #800080;">7774747</span>,<span style="color: #800080;">7774774</span>,<span style="color: #800080;">7774777</span>,<span style="color: #800080;">7777444</span>,<span style="color: #800080;">7777447</span>,<span style="color: #800080;">7777474</span>,<span style="color: #800080;">7777477</span>,<span style="color: #800080;">7777744</span>,<span style="color: #800080;">7777747</span>,<span style="color: #800080;">7777774</span>,<span style="color: #800080;">7777777</span>,<span style="color: #800080;">44444444</span>,<span style="color: #800080;">44444447</span>,<span style="color: #800080;">44444474</span>,<span style="color: #800080;">44444477</span>,<span style="color: #800080;">44444744</span>,<span style="color: #800080;">44444747</span>,<span style="color: #800080;">44444774</span>,<span style="color: #800080;">44444777</span>,<span style="color: #800080;">44447444</span>,<span style="color: #800080;">44447447</span>,<span style="color: #800080;">44447474</span>,<span style="color: #800080;">44447477</span>,<span style="color: #800080;">44447744</span>,<span style="color: #800080;">44447747</span>,<span style="color: #800080;">44447774</span>,<span style="color: #800080;">44447777</span>,<span style="color: #800080;">44474444</span>,<span style="color: #800080;">44474447</span>,<span style="color: #800080;">44474474</span>,<span style="color: #800080;">44474477</span>,<span style="color: #800080;">44474744</span>,<span style="color: #800080;">44474747</span>,<span style="color: #800080;">44474774</span>,<span style="color: #800080;">44474777</span>,<span style="color: #800080;">44477444</span>,<span style="color: #800080;">44477447</span>,<span style="color: #800080;">44477474</span>,<span style="color: #800080;">44477477</span>,<span style="color: #800080;">44477744</span>,<span style="color: #800080;">44477747</span>,<span style="color: #800080;">44477774</span>,<span style="color: #800080;">44477777</span>,<span style="color: #800080;">44744444</span>,<span style="color: #800080;">44744447</span>,<span style="color: #800080;">44744474</span>,<span style="color: #800080;">44744477</span>,<span style="color: #800080;">44744744</span>,<span style="color: #800080;">44744747</span>,<span style="color: #800080;">44744774</span>,<span style="color: #800080;">44744777</span>,<span style="color: #800080;">44747444</span>,<span style="color: #800080;">44747447</span>,<span style="color: #800080;">44747474</span>,<span style="color: #800080;">44747477</span>,<span style="color: #800080;">44747744</span>,<span style="color: #800080;">44747747</span>,<span style="color: #800080;">44747774</span>,<span style="color: #800080;">44747777</span>,<span style="color: #800080;">44774444</span>,<span style="color: #800080;">44774447</span>,<span style="color: #800080;">44774474</span>,<span style="color: #800080;">44774477</span>,<span style="color: #800080;">44774744</span>,<span style="color: #800080;">44774747</span>,<span style="color: #800080;">44774774</span>,<span style="color: #800080;">44774777</span>,<span style="color: #800080;">44777444</span>,<span style="color: #800080;">44777447</span>,<span style="color: #800080;">44777474</span>,<span style="color: #800080;">44777477</span>,<span style="color: #800080;">44777744</span>,<span style="color: #800080;">44777747</span>,<span style="color: #800080;">44777774</span>,<span style="color: #800080;">44777777</span>,<span style="color: #800080;">47444444</span>,<span style="color: #800080;">47444447</span>,<span style="color: #800080;">47444474</span>,<span style="color: #800080;">47444477</span>,<span style="color: #800080;">47444744</span>,<span style="color: #800080;">47444747</span>,<span style="color: #800080;">47444774</span>,<span style="color: #800080;">47444777</span>,<span style="color: #800080;">47447444</span>,<span style="color: #800080;">47447447</span>,<span style="color: #800080;">47447474</span>,<span style="color: #800080;">47447477</span>,<span style="color: #800080;">47447744</span>,<span style="color: #800080;">47447747</span>,<span style="color: #800080;">47447774</span>,<span style="color: #800080;">47447777</span>,<span style="color: #800080;">47474444</span>,<span style="color: #800080;">47474447</span>,<span style="color: #800080;">47474474</span>,<span style="color: #800080;">47474477</span>,<span style="color: #800080;">47474744</span>,<span style="color: #800080;">47474747</span>,<span style="color: #800080;">47474774</span>,<span style="color: #800080;">47474777</span>,<span style="color: #800080;">47477444</span>,<span style="color: #800080;">47477447</span>,<span style="color: #800080;">47477474</span>,<span style="color: #800080;">47477477</span>,<span style="color: #800080;">47477744</span>,<span style="color: #800080;">47477747</span>,<span style="color: #800080;">47477774</span>,<span style="color: #800080;">47477777</span>,<span style="color: #800080;">47744444</span>,<span style="color: #800080;">47744447</span>,<span style="color: #800080;">47744474</span>,<span style="color: #800080;">47744477</span>,<span style="color: #800080;">47744744</span>,<span style="color: #800080;">47744747</span>,<span style="color: #800080;">47744774</span>,<span style="color: #800080;">47744777</span>,<span style="color: #800080;">47747444</span>,<span style="color: #800080;">47747447</span>,<span style="color: #800080;">47747474</span>,<span style="color: #800080;">47747477</span>,<span style="color: #800080;">47747744</span>,<span style="color: #800080;">47747747</span>,<span style="color: #800080;">47747774</span>,<span style="color: #800080;">47747777</span>,<span style="color: #800080;">47774444</span>,<span style="color: #800080;">47774447</span>,<span style="color: #800080;">47774474</span>,<span style="color: #800080;">47774477</span>,<span style="color: #800080;">47774744</span>,<span style="color: #800080;">47774747</span>,<span style="color: #800080;">47774774</span>,<span style="color: #800080;">47774777</span>,<span style="color: #800080;">47777444</span>,<span style="color: #800080;">47777447</span>,<span style="color: #800080;">47777474</span>,<span style="color: #800080;">47777477</span>,<span style="color: #800080;">47777744</span>,<span style="color: #800080;">47777747</span>,<span style="color: #800080;">47777774</span>,<span style="color: #800080;">47777777</span>,<span style="color: #800080;">74444444</span>,<span style="color: #800080;">74444447</span>,<span style="color: #800080;">74444474</span>,<span style="color: #800080;">74444477</span>,<span style="color: #800080;">74444744</span>,<span style="color: #800080;">74444747</span>,<span style="color: #800080;">74444774</span>,<span style="color: #800080;">74444777</span>,<span style="color: #800080;">74447444</span>,<span style="color: #800080;">74447447</span>,<span style="color: #800080;">74447474</span>,<span style="color: #800080;">74447477</span>,<span style="color: #800080;">74447744</span>,<span style="color: #800080;">74447747</span>,<span style="color: #800080;">74447774</span>,<span style="color: #800080;">74447777</span>,<span style="color: #800080;">74474444</span>,<span style="color: #800080;">74474447</span>,<span style="color: #800080;">74474474</span>,<span style="color: #800080;">74474477</span>,<span style="color: #800080;">74474744</span>,<span style="color: #800080;">74474747</span>,<span style="color: #800080;">74474774</span>,<span style="color: #800080;">74474777</span>,<span style="color: #800080;">74477444</span>,<span style="color: #800080;">74477447</span>,<span style="color: #800080;">74477474</span>,<span style="color: #800080;">74477477</span>,<span style="color: #800080;">74477744</span>,<span style="color: #800080;">74477747</span>,<span style="color: #800080;">74477774</span>,<span style="color: #800080;">74477777</span>,<span style="color: #800080;">74744444</span>,<span style="color: #800080;">74744447</span>,<span style="color: #800080;">74744474</span>,<span style="color: #800080;">74744477</span>,<span style="color: #800080;">74744744</span>,<span style="color: #800080;">74744747</span>,<span style="color: #800080;">74744774</span>,<span style="color: #800080;">74744777</span>,<span style="color: #800080;">74747444</span>,<span style="color: #800080;">74747447</span>,<span style="color: #800080;">74747474</span>,<span style="color: #800080;">74747477</span>,<span style="color: #800080;">74747744</span>,<span style="color: #800080;">74747747</span>,<span style="color: #800080;">74747774</span>,<span style="color: #800080;">74747777</span>,<span style="color: #800080;">74774444</span>,<span style="color: #800080;">74774447</span>,<span style="color: #800080;">74774474</span>,<span style="color: #800080;">74774477</span>,<span style="color: #800080;">74774744</span>,<span style="color: #800080;">74774747</span>,<span style="color: #800080;">74774774</span>,<span style="color: #800080;">74774777</span>,<span style="color: #800080;">74777444</span>,<span style="color: #800080;">74777447</span>,<span style="color: #800080;">74777474</span>,<span style="color: #800080;">74777477</span>,<span style="color: #800080;">74777744</span>,<span style="color: #800080;">74777747</span>,<span style="color: #800080;">74777774</span>,<span style="color: #800080;">74777777</span>,<span style="color: #800080;">77444444</span>,<span style="color: #800080;">77444447</span>,<span style="color: #800080;">77444474</span>,<span style="color: #800080;">77444477</span>,<span style="color: #800080;">77444744</span>,<span style="color: #800080;">77444747</span>,<span style="color: #800080;">77444774</span>,<span style="color: #800080;">77444777</span>,<span style="color: #800080;">77447444</span>,<span style="color: #800080;">77447447</span>,<span style="color: #800080;">77447474</span>,<span style="color: #800080;">77447477</span>,<span style="color: #800080;">77447744</span>,<span style="color: #800080;">77447747</span>,<span style="color: #800080;">77447774</span>,<span style="color: #800080;">77447777</span>,<span style="color: #800080;">77474444</span>,<span style="color: #800080;">77474447</span>,<span style="color: #800080;">77474474</span>,<span style="color: #800080;">77474477</span>,<span style="color: #800080;">77474744</span>,<span style="color: #800080;">77474747</span>,<span style="color: #800080;">77474774</span>,<span style="color: #800080;">77474777</span>,<span style="color: #800080;">77477444</span>,<span style="color: #800080;">77477447</span>,<span style="color: #800080;">77477474</span>,<span style="color: #800080;">77477477</span>,<span style="color: #800080;">77477744</span>,<span style="color: #800080;">77477747</span>,<span style="color: #800080;">77477774</span>,<span style="color: #800080;">77477777</span>,<span style="color: #800080;">77744444</span>,<span style="color: #800080;">77744447</span>,<span style="color: #800080;">77744474</span>,<span style="color: #800080;">77744477</span>,<span style="color: #800080;">77744744</span>,<span style="color: #800080;">77744747</span>,<span style="color: #800080;">77744774</span>,<span style="color: #800080;">77744777</span>,<span style="color: #800080;">77747444</span>,<span style="color: #800080;">77747447</span>,<span style="color: #800080;">77747474</span>,<span style="color: #800080;">77747477</span>,<span style="color: #800080;">77747744</span>,<span style="color: #800080;">77747747</span>,<span style="color: #800080;">77747774</span>,<span style="color: #800080;">77747777</span>,<span style="color: #800080;">77774444</span>,<span style="color: #800080;">77774447</span>,<span style="color: #800080;">77774474</span>,<span style="color: #800080;">77774477</span>,<span style="color: #800080;">77774744</span>,<span style="color: #800080;">77774747</span>,<span style="color: #800080;">77774774</span>,<span style="color: #800080;">77774777</span>,<span style="color: #800080;">77777444</span>,<span style="color: #800080;">77777447</span>,<span style="color: #800080;">77777474</span>,<span style="color: #800080;">77777477</span>,<span style="color: #800080;">77777744</span>,<span style="color: #800080;">77777747</span>,<span style="color: #800080;">77777774</span>,<span style="color: #800080;">77777777</span>,<span style="color: #800080;">444444444</span>,<span style="color: #800080;">444444447</span>,<span style="color: #800080;">444444474</span>,<span style="color: #800080;">444444477</span>,<span style="color: #800080;">444444744</span>,<span style="color: #800080;">444444747</span>,<span style="color: #800080;">444444774</span>,<span style="color: #800080;">444444777</span>,<span style="color: #800080;">444447444</span>,<span style="color: #800080;">444447447</span>,<span style="color: #800080;">444447474</span>,<span style="color: #800080;">444447477</span>,<span style="color: #800080;">444447744</span>,<span style="color: #800080;">444447747</span>,<span style="color: #800080;">444447774</span>,<span style="color: #800080;">444447777</span>,<span style="color: #800080;">444474444</span>,<span style="color: #800080;">444474447</span>,<span style="color: #800080;">444474474</span>,<span style="color: #800080;">444474477</span>,<span style="color: #800080;">444474744</span>,<span style="color: #800080;">444474747</span>,<span style="color: #800080;">444474774</span>,<span style="color: #800080;">444474777</span>,<span style="color: #800080;">444477444</span>,<span style="color: #800080;">444477447</span>,<span style="color: #800080;">444477474</span>,<span style="color: #800080;">444477477</span>,<span style="color: #800080;">444477744</span>,<span style="color: #800080;">444477747</span>,<span style="color: #800080;">444477774</span>,<span style="color: #800080;">444477777</span>,<span style="color: #800080;">444744444</span>,<span style="color: #800080;">444744447</span>,<span style="color: #800080;">444744474</span>,<span style="color: #800080;">444744477</span>,<span style="color: #800080;">444744744</span>,<span style="color: #800080;">444744747</span>,<span style="color: #800080;">444744774</span>,<span style="color: #800080;">444744777</span>,<span style="color: #800080;">444747444</span>,<span style="color: #800080;">444747447</span>,<span style="color: #800080;">444747474</span>,<span style="color: #800080;">444747477</span>,<span style="color: #800080;">444747744</span>,<span style="color: #800080;">444747747</span>,<span style="color: #800080;">444747774</span>,<span style="color: #800080;">444747777</span>,<span style="color: #800080;">444774444</span>,<span style="color: #800080;">444774447</span>,<span style="color: #800080;">444774474</span>,<span style="color: #800080;">444774477</span>,<span style="color: #800080;">444774744</span>,<span style="color: #800080;">444774747</span>,<span style="color: #800080;">444774774</span>,<span style="color: #800080;">444774777</span>,<span style="color: #800080;">444777444</span>,<span style="color: #800080;">444777447</span>,<span style="color: #800080;">444777474</span>,<span style="color: #800080;">444777477</span>,<span style="color: #800080;">444777744</span>,<span style="color: #800080;">444777747</span>,<span style="color: #800080;">444777774</span>,<span style="color: #800080;">444777777</span>,<span style="color: #800080;">447444444</span>,<span style="color: #800080;">447444447</span>,<span style="color: #800080;">447444474</span>,<span style="color: #800080;">447444477</span>,<span style="color: #800080;">447444744</span>,<span style="color: #800080;">447444747</span>,<span style="color: #800080;">447444774</span>,<span style="color: #800080;">447444777</span>,<span style="color: #800080;">447447444</span>,<span style="color: #800080;">447447447</span>,<span style="color: #800080;">447447474</span>,<span style="color: #800080;">447447477</span>,<span style="color: #800080;">447447744</span>,<span style="color: #800080;">447447747</span>,<span style="color: #800080;">447447774</span>,<span style="color: #800080;">447447777</span>,<span style="color: #800080;">447474444</span>,<span style="color: #800080;">447474447</span>,<span style="color: #800080;">447474474</span>,<span style="color: #800080;">447474477</span>,<span style="color: #800080;">447474744</span>,<span style="color: #800080;">447474747</span>,<span style="color: #800080;">447474774</span>,<span style="color: #800080;">447474777</span>,<span style="color: #800080;">447477444</span>,<span style="color: #800080;">447477447</span>,<span style="color: #800080;">447477474</span>,<span style="color: #800080;">447477477</span>,<span style="color: #800080;">447477744</span>,<span style="color: #800080;">447477747</span>,<span style="color: #800080;">447477774</span>,<span style="color: #800080;">447477777</span>,<span style="color: #800080;">447744444</span>,<span style="color: #800080;">447744447</span>,<span style="color: #800080;">447744474</span>,<span style="color: #800080;">447744477</span>,<span style="color: #800080;">447744744</span>,<span style="color: #800080;">447744747</span>,<span style="color: #800080;">447744774</span>,<span style="color: #800080;">447744777</span>,<span style="color: #800080;">447747444</span>,<span style="color: #800080;">447747447</span>,<span style="color: #800080;">447747474</span>,<span style="color: #800080;">447747477</span>,<span style="color: #800080;">447747744</span>,<span style="color: #800080;">447747747</span>,<span style="color: #800080;">447747774</span>,<span style="color: #800080;">447747777</span>,<span style="color: #800080;">447774444</span>,<span style="color: #800080;">447774447</span>,<span style="color: #800080;">447774474</span>,<span style="color: #800080;">447774477</span>,<span style="color: #800080;">447774744</span>,<span style="color: #800080;">447774747</span>,<span style="color: #800080;">447774774</span>,<span style="color: #800080;">447774777</span>,<span style="color: #800080;">447777444</span>,<span style="color: #800080;">447777447</span>,<span style="color: #800080;">447777474</span>,<span style="color: #800080;">447777477</span>,<span style="color: #800080;">447777744</span>,<span style="color: #800080;">447777747</span>,<span style="color: #800080;">447777774</span>,<span style="color: #800080;">447777777</span>,<span style="color: #800080;">474444444</span>,<span style="color: #800080;">474444447</span>,<span style="color: #800080;">474444474</span>,<span style="color: #800080;">474444477</span>,<span style="color: #800080;">474444744</span>,<span style="color: #800080;">474444747</span>,<span style="color: #800080;">474444774</span>,<span style="color: #800080;">474444777</span>,<span style="color: #800080;">474447444</span>,<span style="color: #800080;">474447447</span>,<span style="color: #800080;">474447474</span>,<span style="color: #800080;">474447477</span>,<span style="color: #800080;">474447744</span>,<span style="color: #800080;">474447747</span>,<span style="color: #800080;">474447774</span>,<span style="color: #800080;">474447777</span>,<span style="color: #800080;">474474444</span>,<span style="color: #800080;">474474447</span>,<span style="color: #800080;">474474474</span>,<span style="color: #800080;">474474477</span>,<span style="color: #800080;">474474744</span>,<span style="color: #800080;">474474747</span>,<span style="color: #800080;">474474774</span>,<span style="color: #800080;">474474777</span>,<span style="color: #800080;">474477444</span>,<span style="color: #800080;">474477447</span>,<span style="color: #800080;">474477474</span>,<span style="color: #800080;">474477477</span>,<span style="color: #800080;">474477744</span>,<span style="color: #800080;">474477747</span>,<span style="color: #800080;">474477774</span>,<span style="color: #800080;">474477777</span>,<span style="color: #800080;">474744444</span>,<span style="color: #800080;">474744447</span>,<span style="color: #800080;">474744474</span>,<span style="color: #800080;">474744477</span>,<span style="color: #800080;">474744744</span>,<span style="color: #800080;">474744747</span>,<span style="color: #800080;">474744774</span>,<span style="color: #800080;">474744777</span>,<span style="color: #800080;">474747444</span>,<span style="color: #800080;">474747447</span>,<span style="color: #800080;">474747474</span>,<span style="color: #800080;">474747477</span>,<span style="color: #800080;">474747744</span>,<span style="color: #800080;">474747747</span>,<span style="color: #800080;">474747774</span>,<span style="color: #800080;">474747777</span>,<span style="color: #800080;">474774444</span>,<span style="color: #800080;">474774447</span>,<span style="color: #800080;">474774474</span>,<span style="color: #800080;">474774477</span>,<span style="color: #800080;">474774744</span>,<span style="color: #800080;">474774747</span>,<span style="color: #800080;">474774774</span>,<span style="color: #800080;">474774777</span>,<span style="color: #800080;">474777444</span>,<span style="color: #800080;">474777447</span>,<span style="color: #800080;">474777474</span>,<span style="color: #800080;">474777477</span>,<span style="color: #800080;">474777744</span>,<span style="color: #800080;">474777747</span>,<span style="color: #800080;">474777774</span>,<span style="color: #800080;">474777777</span>,<span style="color: #800080;">477444444</span>,<span style="color: #800080;">477444447</span>,<span style="color: #800080;">477444474</span>,<span style="color: #800080;">477444477</span>,<span style="color: #800080;">477444744</span>,<span style="color: #800080;">477444747</span>,<span style="color: #800080;">477444774</span>,<span style="color: #800080;">477444777</span>,<span style="color: #800080;">477447444</span>,<span style="color: #800080;">477447447</span>,<span style="color: #800080;">477447474</span>,<span style="color: #800080;">477447477</span>,<span style="color: #800080;">477447744</span>,<span style="color: #800080;">477447747</span>,<span style="color: #800080;">477447774</span>,<span style="color: #800080;">477447777</span>,<span style="color: #800080;">477474444</span>,<span style="color: #800080;">477474447</span>,<span style="color: #800080;">477474474</span>,<span style="color: #800080;">477474477</span>,<span style="color: #800080;">477474744</span>,<span style="color: #800080;">477474747</span>,<span style="color: #800080;">477474774</span>,<span style="color: #800080;">477474777</span>,<span style="color: #800080;">477477444</span>,<span style="color: #800080;">477477447</span>,<span style="color: #800080;">477477474</span>,<span style="color: #800080;">477477477</span>,<span style="color: #800080;">477477744</span>,<span style="color: #800080;">477477747</span>,<span style="color: #800080;">477477774</span>,<span style="color: #800080;">477477777</span>,<span style="color: #800080;">477744444</span>,<span style="color: #800080;">477744447</span>,<span style="color: #800080;">477744474</span>,<span style="color: #800080;">477744477</span>,<span style="color: #800080;">477744744</span>,<span style="color: #800080;">477744747</span>,<span style="color: #800080;">477744774</span>,<span style="color: #800080;">477744777</span>,<span style="color: #800080;">477747444</span>,<span style="color: #800080;">477747447</span>,<span style="color: #800080;">477747474</span>,<span style="color: #800080;">477747477</span>,<span style="color: #800080;">477747744</span>,<span style="color: #800080;">477747747</span>,<span style="color: #800080;">477747774</span>,<span style="color: #800080;">477747777</span>,<span style="color: #800080;">477774444</span>,<span style="color: #800080;">477774447</span>,<span style="color: #800080;">477774474</span>,<span style="color: #800080;">477774477</span>,<span style="color: #800080;">477774744</span>,<span style="color: #800080;">477774747</span>,<span style="color: #800080;">477774774</span>,<span style="color: #800080;">477774777</span>,<span style="color: #800080;">477777444</span>,<span style="color: #800080;">477777447</span>,<span style="color: #800080;">477777474</span>,<span style="color: #800080;">477777477</span>,<span style="color: #800080;">477777744</span>,<span style="color: #800080;">477777747</span>,<span style="color: #800080;">477777774</span>,<span style="color: #800080;">477777777</span>,<span style="color: #800080;">744444444</span>,<span style="color: #800080;">744444447</span>,<span style="color: #800080;">744444474</span>,<span style="color: #800080;">744444477</span>,<span style="color: #800080;">744444744</span>,<span style="color: #800080;">744444747</span>,<span style="color: #800080;">744444774</span>,<span style="color: #800080;">744444777</span>,<span style="color: #800080;">744447444</span>,<span style="color: #800080;">744447447</span>,<span style="color: #800080;">744447474</span>,<span style="color: #800080;">744447477</span>,<span style="color: #800080;">744447744</span>,<span style="color: #800080;">744447747</span>,<span style="color: #800080;">744447774</span>,<span style="color: #800080;">744447777</span>,<span style="color: #800080;">744474444</span>,<span style="color: #800080;">744474447</span>,<span style="color: #800080;">744474474</span>,<span style="color: #800080;">744474477</span>,<span style="color: #800080;">744474744</span>,<span style="color: #800080;">744474747</span>,<span style="color: #800080;">744474774</span>,<span style="color: #800080;">744474777</span>,<span style="color: #800080;">744477444</span>,<span style="color: #800080;">744477447</span>,<span style="color: #800080;">744477474</span>,<span style="color: #800080;">744477477</span>,<span style="color: #800080;">744477744</span>,<span style="color: #800080;">744477747</span>,<span style="color: #800080;">744477774</span>,<span style="color: #800080;">744477777</span>,<span style="color: #800080;">744744444</span>,<span style="color: #800080;">744744447</span>,<span style="color: #800080;">744744474</span>,<span style="color: #800080;">744744477</span>,<span style="color: #800080;">744744744</span>,<span style="color: #800080;">744744747</span>,<span style="color: #800080;">744744774</span>,<span style="color: #800080;">744744777</span>,<span style="color: #800080;">744747444</span>,<span style="color: #800080;">744747447</span>,<span style="color: #800080;">744747474</span>,<span style="color: #800080;">744747477</span>,<span style="color: #800080;">744747744</span>,<span style="color: #800080;">744747747</span>,<span style="color: #800080;">744747774</span>,<span style="color: #800080;">744747777</span>,<span style="color: #800080;">744774444</span>,<span style="color: #800080;">744774447</span>,<span style="color: #800080;">744774474</span>,<span style="color: #800080;">744774477</span>,<span style="color: #800080;">744774744</span>,<span style="color: #800080;">744774747</span>,<span style="color: #800080;">744774774</span>,<span style="color: #800080;">744774777</span>,<span style="color: #800080;">744777444</span>,<span style="color: #800080;">744777447</span>,<span style="color: #800080;">744777474</span>,<span style="color: #800080;">744777477</span>,<span style="color: #800080;">744777744</span>,<span style="color: #800080;">744777747</span>,<span style="color: #800080;">744777774</span>,<span style="color: #800080;">744777777</span>,<span style="color: #800080;">747444444</span>,<span style="color: #800080;">747444447</span>,<span style="color: #800080;">747444474</span>,<span style="color: #800080;">747444477</span>,<span style="color: #800080;">747444744</span>,<span style="color: #800080;">747444747</span>,<span style="color: #800080;">747444774</span>,<span style="color: #800080;">747444777</span>,<span style="color: #800080;">747447444</span>,<span style="color: #800080;">747447447</span>,<span style="color: #800080;">747447474</span>,<span style="color: #800080;">747447477</span>,<span style="color: #800080;">747447744</span>,<span style="color: #800080;">747447747</span>,<span style="color: #800080;">747447774</span>,<span style="color: #800080;">747447777</span>,<span style="color: #800080;">747474444</span>,<span style="color: #800080;">747474447</span>,<span style="color: #800080;">747474474</span>,<span style="color: #800080;">747474477</span>,<span style="color: #800080;">747474744</span>,<span style="color: #800080;">747474747</span>,<span style="color: #800080;">747474774</span>,<span style="color: #800080;">747474777</span>,<span style="color: #800080;">747477444</span>,<span style="color: #800080;">747477447</span>,<span style="color: #800080;">747477474</span>,<span style="color: #800080;">747477477</span>,<span style="color: #800080;">747477744</span>,<span style="color: #800080;">747477747</span>,<span style="color: #800080;">747477774</span>,<span style="color: #800080;">747477777</span>,<span style="color: #800080;">747744444</span>,<span style="color: #800080;">747744447</span>,<span style="color: #800080;">747744474</span>,<span style="color: #800080;">747744477</span>,<span style="color: #800080;">747744744</span>,<span style="color: #800080;">747744747</span>,<span style="color: #800080;">747744774</span>,<span style="color: #800080;">747744777</span>,<span style="color: #800080;">747747444</span>,<span style="color: #800080;">747747447</span>,<span style="color: #800080;">747747474</span>,<span style="color: #800080;">747747477</span>,<span style="color: #800080;">747747744</span>,<span style="color: #800080;">747747747</span>,<span style="color: #800080;">747747774</span>,<span style="color: #800080;">747747777</span>,<span style="color: #800080;">747774444</span>,<span style="color: #800080;">747774447</span>,<span style="color: #800080;">747774474</span>,<span style="color: #800080;">747774477</span>,<span style="color: #800080;">747774744</span>,<span style="color: #800080;">747774747</span>,<span style="color: #800080;">747774774</span>,<span style="color: #800080;">747774777</span>,<span style="color: #800080;">747777444</span>,<span style="color: #800080;">747777447</span>,<span style="color: #800080;">747777474</span>,<span style="color: #800080;">747777477</span>,<span style="color: #800080;">747777744</span>,<span style="color: #800080;">747777747</span>,<span style="color: #800080;">747777774</span>,<span style="color: #800080;">747777777</span>,<span style="color: #800080;">774444444</span>,<span style="color: #800080;">774444447</span>,<span style="color: #800080;">774444474</span>,<span style="color: #800080;">774444477</span>,<span style="color: #800080;">774444744</span>,<span style="color: #800080;">774444747</span>,<span style="color: #800080;">774444774</span>,<span style="color: #800080;">774444777</span>,<span style="color: #800080;">774447444</span>,<span style="color: #800080;">774447447</span>,<span style="color: #800080;">774447474</span>,<span style="color: #800080;">774447477</span>,<span style="color: #800080;">774447744</span>,<span style="color: #800080;">774447747</span>,<span style="color: #800080;">774447774</span>,<span style="color: #800080;">774447777</span>,<span style="color: #800080;">774474444</span>,<span style="color: #800080;">774474447</span>,<span style="color: #800080;">774474474</span>,<span style="color: #800080;">774474477</span>,<span style="color: #800080;">774474744</span>,<span style="color: #800080;">774474747</span>,<span style="color: #800080;">774474774</span>,<span style="color: #800080;">774474777</span>,<span style="color: #800080;">774477444</span>,<span style="color: #800080;">774477447</span>,<span style="color: #800080;">774477474</span>,<span style="color: #800080;">774477477</span>,<span style="color: #800080;">774477744</span>,<span style="color: #800080;">774477747</span>,<span style="color: #800080;">774477774</span>,<span style="color: #800080;">774477777</span>,<span style="color: #800080;">774744444</span>,<span style="color: #800080;">774744447</span>,<span style="color: #800080;">774744474</span>,<span style="color: #800080;">774744477</span>,<span style="color: #800080;">774744744</span>,<span style="color: #800080;">774744747</span>,<span style="color: #800080;">774744774</span>,<span style="color: #800080;">774744777</span>,<span style="color: #800080;">774747444</span>,<span style="color: #800080;">774747447</span>,<span style="color: #800080;">774747474</span>,<span style="color: #800080;">774747477</span>,<span style="color: #800080;">774747744</span>,<span style="color: #800080;">774747747</span>,<span style="color: #800080;">774747774</span>,<span style="color: #800080;">774747777</span>,<span style="color: #800080;">774774444</span>,<span style="color: #800080;">774774447</span>,<span style="color: #800080;">774774474</span>,<span style="color: #800080;">774774477</span>,<span style="color: #800080;">774774744</span>,<span style="color: #800080;">774774747</span>,<span style="color: #800080;">774774774</span>,<span style="color: #800080;">774774777</span>,<span style="color: #800080;">774777444</span>,<span style="color: #800080;">774777447</span>,<span style="color: #800080;">774777474</span>,<span style="color: #800080;">774777477</span>,<span style="color: #800080;">774777744</span>,<span style="color: #800080;">774777747</span>,<span style="color: #800080;">774777774</span>,<span style="color: #800080;">774777777</span>,<span style="color: #800080;">777444444</span>,<span style="color: #800080;">777444447</span>,<span style="color: #800080;">777444474</span>,<span style="color: #800080;">777444477</span>,<span style="color: #800080;">777444744</span>,<span style="color: #800080;">777444747</span>,<span style="color: #800080;">777444774</span>,<span style="color: #800080;">777444777</span>,<span style="color: #800080;">777447444</span>,<span style="color: #800080;">777447447</span>,<span style="color: #800080;">777447474</span>,<span style="color: #800080;">777447477</span>,<span style="color: #800080;">777447744</span>,<span style="color: #800080;">777447747</span>,<span style="color: #800080;">777447774</span>,<span style="color: #800080;">777447777</span>,<span style="color: #800080;">777474444</span>,<span style="color: #800080;">777474447</span>,<span style="color: #800080;">777474474</span>,<span style="color: #800080;">777474477</span>,<span style="color: #800080;">777474744</span>,<span style="color: #800080;">777474747</span>,<span style="color: #800080;">777474774</span>,<span style="color: #800080;">777474777</span>,<span style="color: #800080;">777477444</span>,<span style="color: #800080;">777477447</span>,<span style="color: #800080;">777477474</span>,<span style="color: #800080;">777477477</span>,<span style="color: #800080;">777477744</span>,<span style="color: #800080;">777477747</span>,<span style="color: #800080;">777477774</span>,<span style="color: #800080;">777477777</span>,<span style="color: #800080;">777744444</span>,<span style="color: #800080;">777744447</span>,<span style="color: #800080;">777744474</span>,<span style="color: #800080;">777744477</span>,<span style="color: #800080;">777744744</span>,<span style="color: #800080;">777744747</span>,<span style="color: #800080;">777744774</span>,<span style="color: #800080;">777744777</span>,<span style="color: #800080;">777747444</span>,<span style="color: #800080;">777747447</span>,<span style="color: #800080;">777747474</span>,<span style="color: #800080;">777747477</span>,<span style="color: #800080;">777747744</span>,<span style="color: #800080;">777747747</span>,<span style="color: #800080;">777747774</span>,<span style="color: #800080;">777747777</span>,<span style="color: #800080;">777774444</span>,<span style="color: #800080;">777774447</span>,<span style="color: #800080;">777774474</span>,<span style="color: #800080;">777774477</span>,<span style="color: #800080;">777774744</span>,<span style="color: #800080;">777774747</span>,<span style="color: #800080;">777774774</span>,<span style="color: #800080;">777774777</span>,<span style="color: #800080;">777777444</span>,<span style="color: #800080;">777777447</span>,<span style="color: #800080;">777777474</span>,<span style="color: #800080;">777777477</span>,<span style="color: #800080;">777777744</span>,<span style="color: #800080;">777777747</span>,<span style="color: #800080;">777777774</span>,<span style="color: #800080;">777777777</span><span style="color: #000000;">};
    </span><span style="color: #0000ff;">bool</span> ok( <span style="color: #0000ff;">int</span><span style="color: #000000;"> x)
    {
        </span><span style="color: #0000ff;">int</span><span style="color: #000000;"> g;
        </span><span style="color: #0000ff;">while</span><span style="color: #000000;"> (x)
        {
            g </span>= x%<span style="color: #800080;">10</span><span style="color: #000000;">;
            x </span>= x/<span style="color: #800080;">10</span><span style="color: #000000;">;
            </span><span style="color: #0000ff;">if</span> (g==<span style="color: #800080;">4</span>||g==<span style="color: #800080;">7</span><span style="color: #000000;">)
                </span><span style="color: #0000ff;">continue</span><span style="color: #000000;">;
            </span><span style="color: #0000ff;">else</span> <span style="color: #0000ff;">return</span> <span style="color: #0000ff;">false</span><span style="color: #000000;">;
        }
        </span><span style="color: #0000ff;">return</span> <span style="color: #0000ff;">true</span><span style="color: #000000;">;
    
    }
    
    
    
    </span><span style="color: #0000ff;">int</span><span style="color: #000000;"> main()
    {
        cin</span>>><span style="color: #000000;">n;
        </span><span style="color: #0000ff;">for</span> ( <span style="color: #0000ff;">int</span> i = <span style="color: #800080;">0</span>;i <= <span style="color: #800080;">99999</span> ; i++<span style="color: #000000;"> )
            </span><span style="color: #0000ff;">if</span> (a[i]==<span style="color: #000000;">n)
        {
            cout</span><<i+<span style="color: #800080;">1</span><<<span style="color: #000000;">endl;
            </span><span style="color: #0000ff;">break</span><span style="color: #000000;">;
        }
    
        </span><span style="color: #0000ff;">return</span> <span style="color: #800080;">0</span><span style="color: #000000;">;
    }</span>






























