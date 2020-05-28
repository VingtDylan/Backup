---
title: LeetCode 287
mathjax: true
copyright: true
tags:
  - LeetCode
  - 双指针
  - 二分查找
categories: LeetCode
abbrlink: 58dd
date: 2020-05-26 00:02:55
---

#### [287. 寻找重复数](https://leetcode-cn.com/problems/find-the-duplicate-number/)

难度:  medium

给定一个包含 *n* + 1 个整数的数组 *nums*，其数字都在 1 到 *n* 之间（包括 1 和 *n*），可知至少存在一个重复的整数。假设只有一个重复的整数，找出这个重复的数。

**示例 1:**

```
输入: [1,3,4,2,2]
输出: 2
```

<!--more-->

**示例 2:**

```
输入: [3,1,3,4,2]
输出: 3
```

**说明：**

1. **不能**更改原数组（假设数组是只读的）。
2. 只能使用额外的 *O*(1) 的空间。
3. 时间复杂度小于 *O*(*n*2) 。
4. 数组中只有一个重复的数字，但它可能不止重复出现一次。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/find-the-duplicate-number
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

弱智的我第一次还以为重复的数字只出现一次，所以累加和...tui

```c++
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int left = 1, right = (int)nums.size() - 1;
        while(left < right){
            int mid = left + right >> 1;
            int co = count(nums,mid);
            if(co <= mid){
                left = mid + 1;
            }else{
                right = mid;
            }
        }
        return left;
    }

    int count(vector<int>& nums, int target){
        int res = 0;
        for(auto num : nums){
            res += target >= num;
        }
        return res;
    }
};
```

