---
title: LeetCode 572
mathjax: true
copyright: true
tags:
  - LeetCode
  - 树
categories: LeetCode
abbrlink: 6aa9
date: 2020-05-07 00:05:29
---

#### [572. 另一个树的子树](https://leetcode-cn.com/problems/subtree-of-another-tree/)

难度: easy

给定两个非空二叉树 s 和 t，检验 s 中是否包含和 t 具有相同结构和节点值的子树。s 的一个子树包括 s 的一个节点和这个节点的所有子孙。s 也可以看做它自身的一棵子树。

示例 1:
给定的树 s:
```
     3
    / \
   4   5
  / \
 1   2
```
给定的树 t：
```
   4 
  / \
 1   2

```
返回 true，因为 t 与 s 的一个子树拥有相同的结构和节点值。

<!--more-->

示例 2:
给定的树 s：

```
     3
    / \
   4   5
  / \
 1   2
    /
   0
```
给定的树 t：
```
   4
  / \
 1   2
```
返回 false。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/subtree-of-another-tree
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

区分好"相同"与"真子树"

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
    bool isSubtree(TreeNode* s, TreeNode* t) {
        if (!s) return false;
        if (isSame(s, t)) return true;
        else return isSubtree(s->left, t) || isSubtree(s->right, t);
    }

    bool isSame(TreeNode* s, TreeNode* t){
        if (!s && !t) return true;
        if (!s || !t) return false;
        if (s->val != t->val) return false;
        return isSame(s->left, t->left) && isSame(s->right, t->right);
    }
};
```
