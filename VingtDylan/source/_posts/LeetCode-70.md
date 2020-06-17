---
title: LeetCode 70
mathjax: true
copyright: true
tags:
  - LeetCode
  - 动态规划
categories: LeetCode
abbrlink: cbeb
date: 2020-06-13 16:42:56
---

#### [70. 爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/)

难度: easy

假设你正在爬楼梯。需要 *n* 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

**注意：**给定 *n* 是一个正整数。

**示例 1：**

```
输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶
```

<!--more-->

**示例 2：**

```
输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/climbing-stairs
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

滚动数组，常见，O(1)空间

```c++
class Solution {
public:
    int climbStairs(int n) {
        if(n == 1)return 1;
        if(n == 2)return 2;
        int pre = 1;
        int cur = 2;
        for(int i = 3; i <= n; i++){
            cur = pre + cur;
            pre = cur - pre;
        }
        return cur;
    }
};
```

