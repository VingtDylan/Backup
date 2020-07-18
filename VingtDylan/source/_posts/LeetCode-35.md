---
title: LeetCode 35
mathjax: true
copyright: true
tags:
  - LeetCode
  - 数组
  - 二分查找
categories: LeetCode
abbrlink: '829'
date: 2020-07-18 15:14:36
---

#### [35. 搜索插入位置](https://leetcode-cn.com/problems/search-insert-position/)

难度: easy

给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

你可以假设数组中无重复元素。

**示例 1:**

```
输入: [1,3,5,6], 5
输出: 2
```

**示例 2:**

```
输入: [1,3,5,6], 2
输出: 1
```

**示例 3:**

```
输入: [1,3,5,6], 7
输出: 4
```

**示例 4:**

```
输入: [1,3,5,6], 0
输出: 0
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/search-insert-position/
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int left = 0, right = nums.size() - 1;
        int mid;
        while(left < right){
            mid = left + (right - left) / 2;
            if(nums[mid] == target)return mid;
            if(nums[mid] > target)right = mid;
            else left = mid + 1;
        }
        if(left == nums.size() - 1 && nums[left] < target)return nums.size();
        return left;
    }
};
```

