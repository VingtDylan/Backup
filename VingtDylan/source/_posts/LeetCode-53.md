---
title: LeetCode 53
mathjax: true
copyright: true
tags:
  - LeetCode
  - 分治
  - 动态规划
categories: LeetCode
abbrlink: aaaa
date: 2020-05-03 12:53:05
---

#### [53. 最大子序和](https://leetcode-cn.com/problems/maximum-subarray/)

难度 easy

给定一个整数数组 `nums` ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

**示例:**

```
输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为6。
```

**进阶:**

如果你已经实现复杂度为 O(**n**) 的解法，尝试使用更为精妙的分治法求解。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/maximum-subarray
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

<!--more-->

#### AC代码

1. O(n)很容易

```c++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int n = nums.size();
        int maxSum = nums[0];
        int sum = 0;
        for(int i = 0; i < n; i++){
            if(sum < 0)sum = nums[i];
            else sum += nums[i];
            maxSum = max(maxSum, sum);
        }
        return maxSum;
    }
};
```

2. 分治算法，并不觉得很强

左子数组max1, 右子数组max2, 从中间向左右延伸max3，求三者最大即可。

```c++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        return divide(nums, 0, (int)nums.size() - 1);
    }

    int divide(vector<int>& nums, int left, int right){
        if(left >= right)return nums[left];
        int mid = left + (right - left) / 2;
        int max1 = divide(nums, left, mid - 1);
        int max2 = divide(nums, mid + 1, right);
        int max3 = nums[mid], tempMax = max3;
        for(int i = mid - 1; i >= left; i--){
            tempMax += nums[i];
            max3 = max(max3, tempMax);
        }
        tempMax = max3;
        for(int i = mid + 1; i <= right; i++){
            tempMax += nums[i];
            max3 = max(max3, tempMax);
        }
        return max(max3, max(max1, max2));
    }
};
```