---
title: LeetCode 693
mathjax: true
copyright: true
tags:
  - LeetCode
  - 位运算
categories: LeetCode
abbrlink: ca9c
date: 2020-07-18 14:44:02
---

#### [693. 交替位二进制数](https://leetcode-cn.com/problems/binary-number-with-alternating-bits/)

难度: easy

给定一个正整数，检查他是否为交替位二进制数：换句话说，就是他的二进制数相邻的两个位数永不相等。

**示例 1:**

```
输入: 5
输出: True
解释:
5的二进制数是: 101
```

**示例 2:**

```
输入: 7
输出: False
解释:
7的二进制数是: 111
```

**示例 3:**

```
输入: 11
输出: False
解释:
11的二进制数是: 1011
```

 **示例 4:**

```
输入: 10
输出: True
解释:
10的二进制数是: 1010
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/valid-palindrome-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    bool hasAlternatingBits(int n) {
        if(n == 1)return true;
        return ((n & 1) != ((n >> 1) & 1)) && hasAlternatingBits(n >> 1);
    }
};
```





