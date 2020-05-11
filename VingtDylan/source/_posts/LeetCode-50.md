---
title: LeetCode 50
mathjax: true
copyright: true
abbrlink: abea
date: 2020-05-11 00:04:14
tags:
  - LeetCode
  - 数学
  - 二分查找
categories: LeetCode
---

#### [50. Pow(x, n)](https://leetcode-cn.com/problems/powx-n/)

难度: medium

实现 [pow(*x*, *n*)](https://www.cplusplus.com/reference/valarray/pow/) ，即计算 x 的 n 次幂函数。

**示例 1:**

```
输入: 2.00000, 10
输出: 1024.00000
```

<!--more-->

**示例 2:**

```
输入: 2.10000, 3
输出: 9.26100
```

**示例 3:**

```
输入: 2.00000, -2
输出: 0.25000
解释: 2-2 = 1/22 = 1/4 = 0.25
```

**说明:**

- -100.0 < *x* < 100.0
- *n* 是 32 位有符号整数，其数值范围是 [−231, 231 − 1] 。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/powx-n
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

快速幂迭代也不难，懒得写了

注意INT_MIN这个点就行了，也就是1/pow(x,-n)是要考虑范围的

顺便，快速幂是二分查找的意思么？感觉牵强

```c++
class Solution {
public:
    double myPow(double x, int n) {
        // x == 0???
        // n = -2147483648
        if(n == 0)return 1.0;
        if(n == 1)return x;
        double half = myPow(x, n / 2);
        if(n % 2 == 0)return half * half;
        if(n > 0)return half * half * x;
        return half * half / x;
    }
};
```

