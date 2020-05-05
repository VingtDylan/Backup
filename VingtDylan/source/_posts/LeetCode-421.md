---
title: LeetCode 421
mathjax: true
copyright: true
tags:
  - LeetCode
  - 位运算
  - Trie树
  - 贪心
categories:
  - LeetCode
abbrlink: fbbb
date: 2020-03-09 18:59:08
---

#### [421. 数组中两个数的最大异或值](https://leetcode-cn.com/problems/maximum-xor-of-two-numbers-in-an-array/)

给定一个非空数组，数组中元素为 $a_0, a_1, a_2, … , a_{n-1}$，其中 $0 \leq a_i < 231$ 。

找到 $a_i$ 和$a_j$ 最大的异或 (XOR) 运算结果，其中$0 \leq i,  j < n$ 。

你能在O(n)的时间解决这个问题吗？

**示例**:

```
输入: [3, 10, 5, 25, 2, 8]

输出: 28

解释: 最大的结果是 5 ^ 25 = 28.
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/maximum-xor-of-two-numbers-in-an-array
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### 思路：贪心

