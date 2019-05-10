---
author: 111qqz
date: 2015-07-29 13:51:00+00:00
draft: false
title: SPOJ AMR10F Cookies Piles
type: post
url: /2015/07/spojamr10fcookiespiles/
categories:
- sgu
---

## AMR10F - Cookies Piles







_no tags_













The kids in my son's kindergarten made Christmas cookies with their teacher, and piled them up in columns. They then arranged the columns so that the tops of the columns, going from shortest to tallest, were in a nice straight ramp. The cookies were all of uniform size. Given that there were A cookies in the shortest pile, that the difference in height between any two adjacent piles was D cookies, and that there were N piles, can you write a program to figure out how many cookies there were in total?   
  
INPUT   
The first line contains the number of test cases T. T lines follow, one corresponding to each test case, containing 3 integers : N, A and D.   
  
OUTPUT  
Output T lines, each line containing the required answer for the corresponding test case.   
  
CONSTRAINTS   
T <= 100   
1 <= N, A, D <=100   
  
SAMPLE INPUT   
3   
1 1 1   
3 5 6   
2 1 2   
  
SAMPLE OUTPUT   
1   
33   
4   
  
EXPLANATION   
In the second test case the sequence is: 5, 11, 17 whose sum is 33.








[ Submit solution!](http://www.spoj.com/submit/AMR10F/)







水.



    

    
    /*************************************************************************
    	> File Name: code/2015summer/#4/F.cpp
    	> Author: 111qqz
    	> Email: rkz2013@126.com 
    	> Created Time: 2015年07月29日 星期三 21时47分23秒
     ************************************************************************/
    
    #include<iostream>
    #include<iomanip>
    #include<cstdio>
    #include<algorithm>
    #include<cmath>
    #include<cstring>
    #include<string>
    #include<map>
    #include<set>
    #include<queue>
    #include<vector>
    #include<stack>
    #define y0 abc111qqz
    #define y1 hust111qqz
    #define yn hez111qqz
    #define j1 cute111qqz
    #define tm crazy111qqz
    #define lr dying111qqz
    using namespace std;
    #define REP(i, n) for (int i=0;i<int(n);++i)  
    typedef long long LL;
    typedef unsigned long long ULL;
    const int inf = 0x7fffffff;
    int main()
    {
        int T;
        int n,a,d;
        cin>>T;
        while (T--)
        {
    	scanf("%d %d %d",&n,&a,&d);
    	cout<<n*a+n*(n-1)/2*d<<endl;
        }
      
    	return 0;
    }
    



