---
title: LeetCode 95
mathjax: true
copyright: true
tags:
  - LeetCode
  - 树
  - 动态规划
categories: LeetCode
abbrlink: a82f
date: 2020-05-08 22:39:06
---

#### [95. 不同的二叉搜索树 II](https://leetcode-cn.com/problems/unique-binary-search-trees-ii/)

难度: medium

给定一个整数 *n* ，生成所有由 1 ... *n*  为节点所组成的**二叉搜索树**。

**示例:**

```
输入: 3
输出:
[
  [1,null,3,2],
  [3,2,null,1],
  [3,1,null,null,2],
  [2,1,3],
  [1,null,2,null,3]
]
解释:
以上的输出对应以下 5 种不同结构的二叉搜索树：

   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/unique-binary-search-trees-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

常规分治

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
    vector<TreeNode*> generateTrees(int n) {
        if(n < 1)return {};
        return divide(1, n);
    }

    vector<TreeNode*> divide(int left, int right){
        if(left > right)return {nullptr};
        vector<TreeNode*> res;
        for(int i = left; i <= right; i++){
            auto leftTree = divide(left, i - 1);
            auto rightTree = divide(i + 1, right);
            for(auto leftSubTree : leftTree){
                for(auto rightSubTree: rightTree){
                    TreeNode* root = new TreeNode(i);
                    root->left = leftSubTree;
                    root->right = rightSubTree;
                    res.push_back(root);
                }
            }
        }
        return res;
    }
};
```

#### 强行动规

不想写了，用一个二维$vector$,$vec[i][j]$记录区间i到j所有可以生成的BST的根节点。