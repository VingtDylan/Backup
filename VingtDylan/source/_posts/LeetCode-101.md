---
title: LeetCode 101
mathjax: true
copyright: true
tags:
  - LeetCode
  - 树
  - 深度优先搜索
  - 广度优先搜索
categories: LeetCode
abbrlink: 9aaa
date: 2020-05-31 10:37:22
---

#### [101. 对称二叉树](https://leetcode-cn.com/problems/symmetric-tree/)

难度: easy

给定一个二叉树，检查它是否是镜像对称的。

例如，二叉树 `[1,2,2,3,4,4,3]` 是对称的。

```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```

但是下面这个 `[1,2,2,null,3,null,3]` 则不是镜像对称的:

```
    1
   / \
  2   2
   \   \
   3    3
```

**进阶：**

你可以运用递归和迭代两种方法解决这个问题吗？

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/symmetric-tree
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

迭代水一下

```c++
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
    bool isSymmetric(TreeNode* root) {
        if(!root)return true;
        return isSymmetricSubTree(root->left,root->right);
    }

    bool isSymmetricSubTree(TreeNode* left, TreeNode* right){
        if(!left && !right)return true;
        if(!left || !right)return false;
        if(left->val != right->val)return false;
        return isSymmetricSubTree(left->left,right->right) && isSymmetricSubTree(left->right,right->left);
    }
};
```

