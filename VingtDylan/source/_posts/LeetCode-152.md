---
title: LeetCode 152
mathjax: true
copyright: true
tags:
  - LeetCode
  - 数组
  - 动态规划
categories: LeetCode
abbrlink: cbe9
date: 2020-05-18 00:03:16
---

#### [152. 乘积最大子数组](https://leetcode-cn.com/problems/maximum-product-subarray/)

难度: medium

给你一个整数数组 `nums` ，请你找出数组中乘积最大的连续子数组（该子数组中至少包含一个数字），并返回该子数组所对应的乘积。

**示例 1:**

```
输入: [2,3,-2,4]
输出: 6
解释: 子数组 [2,3] 有最大乘积 6。
```

<!--more-->

**示例 2:**

```
输入: [-2,0,-1]
输出: 0
解释: 结果不能为 2, 因为 [-2,-1] 不是子数组。
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/maximum-product-subarray
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int n = nums.size();
        int res = nums[0];
        vector<int> dp1(n,0);dp1[0] = nums[0];
        vector<int> dp2(n,0);dp2[0] = nums[0];
        for(int i = 1; i < n; i++){
            dp1[i] = max(max(nums[i], dp1[i - 1] * nums[i]), dp2[i - 1] * nums[i]);
            dp2[i] = min(min(nums[i], dp1[i - 1] * nums[i]), dp2[i - 1] * nums[i]);
            res = max(dp1[i],res);
        }
        return res;
    }
};
```



