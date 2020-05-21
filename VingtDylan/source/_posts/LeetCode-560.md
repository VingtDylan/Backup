---
title: LeetCode 560
mathjax: true
copyright: true
tags:
  - LeetCode
  - 数组
  - 哈希表
categories: LeetCode
abbrlink: 3b29
date: 2020-05-15 00:32:30
---

#### [560. 和为K的子数组](https://leetcode-cn.com/problems/subarray-sum-equals-k/)

难度: medium

给定一个整数数组和一个整数 **k，**你需要找到该数组中和为 **k** 的连续的子数组的个数。

**示例 1 :**

```
输入:nums = [1,1,1], k = 2
输出: 2 , [1,1] 与 [1,1] 为两种不同的情况。
```

**说明 :**

1. 数组的长度为 [1, 20,000]。
2. 数组中元素的范围是 [-1000, 1000] ，且整数 **k** 的范围是 [-1e7, 1e7]。

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/subarray-sum-equals-k
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        // TLE 
        // TLE的输入太过酸爽
        // int res = 0;
        // int n = nums.size();
        // vector<int> sums(n);
        // sums[0] = nums[0];
        // for(int i = 1; i < n; i++){
        //     sums[i] = sums[i - 1] + nums[i];
        // }
        // for(int i = 0; i < n; i++){
        //     if(sums[i] == k)res++;
        //     for(int j = i - 1; j >= 0; j--){
        //         if(sums[i] - sums[j] == k)
        //             res++;
        //     }
        // }
        // return res;
        int res = 0, sum = 0, n = nums.size();
        unordered_map<int,int> mp{{0,1}};
        for(int i = 0; i < n; i++){
            sum += nums[i];
            res += mp[sum - k];
            mp[sum]++;
        }
        return res;
    }
};
```

