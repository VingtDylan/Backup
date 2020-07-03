---
title: LeetCode 41
mathjax: true
copyright: true
tags:
  - LeetCode
  - 数组
categories: LeetCode
abbrlink: fb2a
date: 2020-06-27 14:19:34
---

#### [41. 缺失的第一个正数](https://leetcode-cn.com/problems/first-missing-positive/)

难度: hard

给你一个未排序的整数数组，请你找出其中没有出现的最小的正整数。

**示例 1:**

```
输入: [1,2,0]
输出: 3
```

<!--more-->

**示例 2:**

```
输入: [3,4,-1,1]
输出: 2
```

**示例 3:**

```
输入: [7,8,9,11,12]
输出: 1
```

**提示：**

你的算法的时间复杂度应为O(*n*)，并且只能使用常数级别的额外空间。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/first-missing-positive
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### 思路

$Position_i$放元素$i +1$,第一次通过swap换位置，第二次遍历找到缺失值。

```c++
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        int n = nums.size();
        for(int i = 0; i < n; i++){
            while(nums[i] > 0 && nums[i] <= n && nums[nums[i] - 1] != nums[i]){
                swap(nums[nums[i] - 1],nums[i]);
            }
        }
        for(int i = 0; i < n; i++){
            if(nums[i] != i + 1)
                return i + 1;
        }
        return n + 1;
    }
};
```

