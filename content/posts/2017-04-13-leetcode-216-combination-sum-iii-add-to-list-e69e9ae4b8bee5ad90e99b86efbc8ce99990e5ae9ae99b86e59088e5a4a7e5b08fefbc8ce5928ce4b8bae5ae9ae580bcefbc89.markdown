---
author: 111qqz
date: 2017-04-13 07:55:09+00:00
draft: false
title: leetcode 216. Combination Sum III Add to List (枚举子集，限定集合大小，和为定值）
type: post
url: /2017/04/leetcode-216-combination-sum-iii-add-to-list-%e6%9e%9a%e4%b8%be%e5%ad%90%e9%9b%86%ef%bc%8c%e9%99%90%e5%ae%9a%e9%9b%86%e5%90%88%e5%a4%a7%e5%b0%8f%ef%bc%8c%e5%92%8c%e4%b8%ba%e5%ae%9a%e5%80%bc%ef%bc%89/
categories:
- leetcode
tags:
- 枚举子集
---



Find all possible combinations of _**k**_ numbers that add up to a number _**n**_, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.

题意：1..9个数，从中选择k个，和为n，要求输出所有满足题意的集合。

思路：枚举子集，根据sum和集合元素个数剪枝即可。

    
    /* ***********************************************
    Author :111qqz
    Created Time :2017年04月13日 星期四 15时44分56秒
    File Name :216.cpp
    ************************************************ */
    class Solution {
    public:
        set<vector<int> >se;
        vector<vector<int> >res;
        int B[1005];
        void get_subset(int n,int *B,int cur,int cnt,int k,int sum,int tar)
        {
    	if (cur==n)
    	{
    	    if (cnt!=k||sum!=tar) return;
    	    vector<int>tmp;
    	    for ( int i = 0 ; i < n ; i++)
    		if (B[i]) tmp.push_back(i+1);
    	    se.insert(tmp);
    	    return ;
    	}
    	if (cnt+1<=k&&sum+(cur+1)<=tar)
    	{
    	    B[cur] = 1;
    	    get_subset(n,B,cur+1,cnt+1,k,sum+(cur+1),tar);
    	}
    	B[cur] = 0 ;
    	get_subset(n,B,cur+1,cnt,k,sum,tar);
        }
        vector<vector<int>> combinationSum3(int k, int n) {
    	get_subset(9,B,0,0,k,0,n);
    	for ( auto &it : se) res.push_back(it);
    	return res;
        }
    };
    





