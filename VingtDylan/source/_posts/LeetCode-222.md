---
title: LeetCode 222
mathjax: true
copyright: true
tags:
  - LeetCode
  - 树
  - 二分查找
categories: LeetCode
abbrlink: fb1b
date: 2020-05-08 00:48:05
---

#### [222. 完全二叉树的节点个数](https://leetcode-cn.com/problems/count-complete-tree-nodes/)

难度:  medium

给出一个**完全二叉树**，求出该树的节点个数。

**说明：**

[完全二叉树](https://baike.baidu.com/item/完全二叉树/7773232?fr=aladdin)的定义如下：在完全二叉树中，除了最底层节点可能没填满外，其余每层节点数都达到最大值，并且最下面一层的节点都集中在该层最左边的若干位置。若最底层为第 h 层，则该层包含 1~ 2h 个节点。

**示例:**

```
输入: 
    1
   / \
  2   3
 / \  /
4  5 6

输出: 6
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/count-complete-tree-nodes
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

<!--more-->

#### AC代码

???这题有意义？

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
    int countNodes(TreeNode* root) {
        if(!root)return 0;
        return 1 + countNodes(root->left) + countNodes(root->right);
    }
};
```

#### 二分代码

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
    int countNodes(TreeNode* root) {
        int res = 0;
        int h = getHeight(root);
        if(h < 0)return 0;
        if(getHeight(root->right) == h - 1)return (1 << h) + countNodes(root->right);
        return (1 << (h - 1)) + countNodes(root->left);
    }

    int getHeight(TreeNode* root){
        return root ? 1 + getHeight(root->left) : -1;
    }
};
```

