---
title: LeetCode 589
mathjax: true
copyright: true
tags:
  - LeetCode
  - 树
categories: LeetCode
abbrlink: 5ded
date: 2020-05-08 22:59:42
---

#### [589. N叉树的前序遍历](https://leetcode-cn.com/problems/n-ary-tree-preorder-traversal/)

难度: easy

给定一个 N 叉树，返回其节点值的*前序遍历*。

例如，给定一个 `3叉树` :

 

![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/narytreeexample.png)

 

返回其前序遍历: `[1,3,5,6,2,4]`。

 <!--more-->

**说明:** 递归法很简单，你可以使用迭代法完成此题吗?

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/n-ary-tree-preorder-traversal
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> children;

    Node() {}

    Node(int _val) {
        val = _val;
    }

    Node(int _val, vector<Node*> _children) {
        val = _val;
        children = _children;
    }
};
*/

class Solution {
public:
    vector<int> preorder(Node* root) {
        vector<int> res;
        process(root, res);
        return res;
    }

    void process(Node* root, vector<int>& res){
        if(!root)return;
        res.push_back(root->val);
        for(int i = 0; i < root->children.size(); i++){
            process(root->children[i],res);
        }
    }
};
```
#### 迭代(可以但没必要)