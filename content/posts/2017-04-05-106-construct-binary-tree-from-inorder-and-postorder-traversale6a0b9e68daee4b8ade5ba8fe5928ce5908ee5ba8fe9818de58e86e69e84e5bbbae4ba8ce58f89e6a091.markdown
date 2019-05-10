---
author: 111qqz
date: 2017-04-05 08:59:41+00:00
draft: false
title: 106. Construct Binary Tree from Inorder and Postorder Traversal(根据中序和后序遍历构建二叉树)
type: post
url: /2017/04/106-construct-binary-tree-from-inorder-and-postorder-traversal%e6%a0%b9%e6%8d%ae%e4%b8%ad%e5%ba%8f%e5%92%8c%e5%90%8e%e5%ba%8f%e9%81%8d%e5%8e%86%e6%9e%84%e5%bb%ba%e4%ba%8c%e5%8f%89%e6%a0%91/
categories:
- leetcode
---

/* ***********************************************
    Author :111qqz
    Created Time :2017年04月05日 星期三 16时49分57秒
    File Name :106.cpp
    ************************************************ */
    /**
     * Definition for a binary tree node.
     * struct TreeNode {
     *     int val;
     *     TreeNode *left;
     *     TreeNode *right;
     *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
     * };
     */
    class Solution {
    public:
        TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
    	int siz = inorder.size();
    	if (siz==0) return NULL;
    	int rt = postorder[siz-1];
    	int pos = -1;
    	for ( int i = 0 ; i < siz;  i++)
    	{
    	    if (inorder[i]==rt)
    	    {
    		pos = i ;
    		break;
    	    }
    	}
    	TreeNode *head = new TreeNode(rt);
    	vector<int>in,post;
    	for ( int i = 0 ; i < pos ; i++)
    	{
    	    in.push_back(inorder[i]);
    	    post.push_back(postorder[i]);
    	}
    	head->left = buildTree(in,post);
    	in.clear();
    	post.clear();
    	for ( int i = pos + 1 ; i < siz ; i++)
    	{
    	    in.push_back(inorder[i]);
    	    post.push_back(postorder[i-1]);
    	}
    	head->right = buildTree(in,post);
    	return head;
        }
    };
    



