---
title: LeetCode 124
mathjax: true
copyright: true
tags:
  - LeetCode
  - 树
  - 深度优先搜索
categories: LeetCode
abbrlink: f96b
date: 2020-06-21 12:49:17
---

#### [124. 二叉树中的最大路径和](https://leetcode-cn.com/problems/binary-tree-maximum-path-sum/)

难度: hard

给定一个**非空**二叉树，返回其最大路径和。

本题中，路径被定义为一条从树中任意节点出发，达到任意节点的序列。该路径**至少包含一个**节点，且不一定经过根节点。

**示例 1:**

```
输入: [1,2,3]

       1
      / \
     2   3

输出: 6
```

<!--more-->

**示例 2:**

```
输入: [-10,9,20,null,null,15,7]

   -10
   / \
  9  20
    /  \
   15   7

输出: 42
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/binary-tree-maximum-path-sum
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

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
    int ans;
    int maxPathSum(TreeNode* root) {
        ans = root->val;
        process(root);
        return ans;
    }
    int process(TreeNode* root){
        if(!root)return 0;
        int leftSum = max(0,process(root->left));
        int rightSum = max(0,process(root->right));
        ans= max(ans,leftSum + rightSum + root->val);
        return root->val + max(leftSum,rightSum);
    }
};
```

