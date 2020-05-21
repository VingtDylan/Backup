---
title: LeetCode 105
mathjax: true
copyright: true
tags:
  - LeetCode
  - 树
  - 深度优先搜索
  - 数组
categories: LeetCode
abbrlink: 59ab
date: 2020-05-22 00:39:05
---

#### [105. 从前序与中序遍历序列构造二叉树](https://leetcode-cn.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

难度: medium

根据一棵树的前序遍历与中序遍历构造二叉树。

**注意:**
你可以假设树中没有重复的元素。

例如，给出

```
前序遍历 preorder = [3,9,20,15,7]
中序遍历 inorder = [9,3,15,20,7]
```

返回如下的二叉树：

```
    3
   / \
  9  20
    /  \
   15   7
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

写个递归拉到了，迭代懒得写，以后补吧

同样的问题还有很多，需要说明的是，迭代才有点难度，尤其是涉及后序遍历相关的问题

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
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        if(preorder.empty() || inorder.empty() || preorder.size() != inorder.size())return NULL;
        int len1 = preorder.size(), len2 = inorder.size();
        return process(preorder, inorder, 0, len1 - 1, 0, len2 - 1);
    }

    TreeNode* process(vector<int>& preorder, vector<int>& inorder,int l1, int r1, int l2, int r2){
        if(l1 > r1 || l2 > r2)return NULL;
        int rootValue = preorder[l1];
        TreeNode* root = new TreeNode(rootValue);
        TreeNode* leftNode = NULL, *rightNode = NULL;
        int index = l2;
        while(inorder[index] != rootValue && index <= r2)index++;
        if(index > l2){
            leftNode = process(preorder, inorder, l1 + 1, l1 + index - l2, l2, index - 1);
        }
        if(index < r2){
            rightNode = process(preorder, inorder, l1 + index - l2 + 1, r1, index + 1, r2);
        }
        root->left = leftNode;
        root->right = rightNode;
        return root;
    }
};
```