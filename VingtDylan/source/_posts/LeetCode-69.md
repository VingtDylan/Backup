---
title: LeetCode 69
mathjax: true
copyright: true
tags: — LeetCode - 二分查找 -  数学
categories: LeetCode
abbrlink: 5d2a
date: 2020-05-09 00:01:40
---

#### [69. x 的平方根](https://leetcode-cn.com/problems/sqrtx/)

难度: easy

实现 `int sqrt(int x)` 函数。

计算并返回 *x* 的平方根，其中 *x* 是非负整数。

由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。

**示例 1:**

```
输入: 4
输出: 2
```

<!--more-->

**示例 2:**

```
输入: 8
输出: 2
说明: 8 的平方根是 2.82842..., 
     由于返回类型是整数，小数部分将被舍去。
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/sqrtx
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码
强行回顾一波...

##### 袖珍计算器算法

```c++
class Solution {
public:
    int mySqrt(int x) {
        if(x == 0)return 0;
        int ans = exp(0.5 * log(x));
        return (long long)(ans + 1) * (ans + 1) <= x ? ans + 1 : ans;
    }
};
```
##### 牛顿切线
```c++
class Solution {
public:
    int mySqrt(int x) {
        if(x == 0)return 0;
        double x0 = x / 2.0;
        while(abs(x0 - (x / x0)) > 1e-7){
            x0 = (x0 + x / x0) / 2;
        }
        return (int)x0;
    }
};
```
##### 二分查找

```c++
class Solution {
public:
    int mySqrt(int x) {
        if(x == 0)return 0;
        double left = 0.0, right = x;
        while(right - left >= 1e-7){
            double mid = (left + right) / 2.0;
            if(mid * mid > x)right = mid;
            else left = mid;
        } 
        return (int)(right);
    }
};
```

