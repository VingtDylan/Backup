---
title: LeetCode 4
mathjax: true
copyright: true
tags:
  - LeetCode
  - 数组
  - 二分查找
  - 分治算法
  - mark
categories: LeetCode
abbrlink: 6b6a
date: 2020-05-24 00:47:32
---

#### [4. 寻找两个正序数组的中位数](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/)

难度: hard

给定两个大小为 m 和 n 的正序（从小到大）数组 `nums1` 和 `nums2`。

请你找出这两个正序数组的中位数，并且要求算法的时间复杂度为 O(log(m + n))。

你可以假设 `nums1` 和 `nums2` 不会同时为空。

**示例 1:**

```
nums1 = [1, 3]
nums2 = [2]

则中位数是 2.0
```

<!--more-->

**示例 2:**

```
nums1 = [1, 2]
nums2 = [3, 4]

则中位数是 (2 + 3)/2 = 2.5
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/median-of-two-sorted-arrays
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

查找两次

m = nums1.size(), n = nums2.size()

trick: 中位数则为:((m+n+1)/2 + (m+n+2)/2)/2.0

对空间的优化以后补充(如果想起来的话)

细节的优化处真是有点烦人

```c++
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int m = nums1.size(), n = nums2.size();
        int mean1 = (m + n + 1) / 2, mean2 = (m + n + 2) / 2;
        return (process(nums1,nums2,mean1) + process(nums1,nums2,mean2))/ 2.0; 
    }

    int process(vector<int> nums1, vector<int> nums2,int k){
        if(nums1.empty())return nums2[k - 1];
        if(nums2.empty())return nums1[k - 1];
        if(k == 1)return min(nums1[0],nums2[0]);
        //divide and conquer
        int midk1 = min((int)nums1.size(), k / 2);
        int midk2 = min((int)nums2.size(), k / 2);
        if(nums1[midk1 - 1] > nums2[midk2 - 1]){
            return process(nums1,vector<int>(nums2.begin() + midk2, nums2.end()), k - midk2);
        }else{
            return process(vector<int>(nums1.begin() + midk1, nums1.end()), nums2, k - midk1);
        }
        return 0;
    }
};
```