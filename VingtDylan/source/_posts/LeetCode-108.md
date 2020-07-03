---
title: LeetCode 108
mathjax: true
copyright: true
tags:
  - LeetCode
  - 树
  - 深度优先搜索
categories: LeetCode
abbrlink: 9c6a
date: 2020-07-03 23:05:30
---

#### [108. 将有序数组转换为二叉搜索树](https://leetcode-cn.com/problems/convert-sorted-array-to-binary-search-tree/)

难度: easy

将一个按照升序排列的有序数组，转换为一棵高度平衡二叉搜索树。

本题中，一个高度平衡二叉树是指一个二叉树*每个节点* 的左右两个子树的高度差的绝对值不超过 1。

**示例:**

```
给定有序数组: [-10,-3,0,5,9],

一个可能的答案是：[0,-3,9,-10,null,5]，它可以表示下面这个高度平衡二叉搜索树：

      0
     / \
   -3   9
   /   /
 -10  5
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/convert-sorted-array-to-binary-search-tree
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
    TreeNode* sortedArrayToBST(vector<int>& nums) {
        return Process(nums,0,nums.size() - 1);
    }

    TreeNode* Process(vector<int>& nums, int left,int right){
        if(left > right)return NULL;
        int mid = left + (right - left) / 2;
        TreeNode* middle = new TreeNode(nums[mid]);
        middle->left = Process(nums,left,mid - 1);
        middle->right = Process(nums,mid + 1,right);
        return middle;
    }
};
```

