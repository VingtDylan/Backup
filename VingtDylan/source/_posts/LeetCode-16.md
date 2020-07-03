---
title: LeetCode 16
mathjax: true
copyright: true
tags:
  - LeetCode
  - 数组
  - 双指针
categories: LeetCode
abbrlink: '6968'
date: 2020-06-24 00:11:20
---

#### [16. 最接近的三数之和](https://leetcode-cn.com/problems/3sum-closest/)

难度: medium

给定一个包括 *n* 个整数的数组 `nums` 和 一个目标值 `target`。找出 `nums` 中的三个整数，使得它们的和与 `target` 最接近。返回这三个数的和。假定每组输入只存在唯一答案。

**示例：**

```
输入：nums = [-1,2,1,-4], target = 1
输出：2
解释：与 target 最接近的和是 2 (-1 + 2 + 1 = 2) 。
```

**提示：**

- `3 <= nums.length <= 10^3`

- `-10^3 <= nums[i] <= 10^3`

- `-10^4 <= target <= 10^4`

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/3sum-closest
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

####  AC代码

```c++
class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        sort(nums.begin(),nums.end());
        int closest = nums[0] + nums[1] + nums[2];
        int diff = abs(closest - target);
        for(int i = 0; i < nums.size() - 2; i++){
            if(nums[i] * 3 > target){
                return min(closest, nums[i] + nums[i + 1] + nums[i + 2]);
            }
            int left = i + 1, right = nums.size() - 1;
            while(left < right){
                int sum = nums[i] + nums[left] + nums[right];
                if(sum < target)left++;
                else if(sum > target) right--;
                else return sum;
                int subdiff = abs(sum - target);
                if(subdiff < diff){
                    diff = subdiff;
                    closest = sum;
                }
            }
        }
        return closest;
    }
};
```

