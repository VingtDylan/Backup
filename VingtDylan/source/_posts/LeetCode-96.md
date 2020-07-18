---
title: LeetCode 96
mathjax: true
copyright: true
tags:
  - LeetCode
  - 树
  - 动态规划
categories: LeetCode
abbrlink: a96f
date: 2020-07-18 15:14:21
---

#### [96. 不同的二叉搜索树](https://leetcode-cn.com/problems/unique-binary-search-trees/)

难度: medium

给定一个整数 *n*，求以 1 ... *n* 为节点组成的二叉搜索树有多少种？

**示例:**

```
输入: 3
输出: 5
解释:
给定 n = 3, 一共有 5 种不同结构的二叉搜索树:

   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/unique-binary-search-trees/
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    int numTrees(int n) {
        vector<int> res(n + 1, 0);
        res[0] = 1, res[1] = 1;
        for(int i = 2; i <= n; i++)
            for(int j = 0; j <= i - 1; j++)
                res[i] += res[j] * res[i - 1 - j];
        return res[n];
    }
};
```

