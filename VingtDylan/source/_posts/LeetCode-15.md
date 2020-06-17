---
title: LeetCode 15
mathjax: true
copyright: true
tags:
  - LeetCode
  - 数组
  - 双指针
categories: LeetCode
abbrlink: '6828'
date: 2020-06-12 00:04:41
---

#### [15. 三数之和](https://leetcode-cn.com/problems/3sum/)

难度: medium

给你一个包含 *n* 个整数的数组 `nums`，判断 `nums` 中是否存在三个元素 *a，b，c ，*使得 *a + b + c =* 0 ？请你找出所有满足条件且不重复的三元组。

**注意：**答案中不可以包含重复的三元组。

**示例：**

```
给定数组 nums = [-1, 0, 1, 2, -1, -4]，

满足要求的三元组集合为：
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/3sum
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

####  AC代码

```c+
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> res;
        sort(nums.begin(), nums.end());
        if(nums.empty() || nums.back() < 0 || nums.front() > 0) return {};
        for(int i = 0; i < (int)nums.size() - 2; i++){
            if(nums[i] > 0) break;
            if(i > 0 && nums[i] == nums[i - 1]) continue;
            int tempTarget = 0 - nums[i]; 
            int j = i + 1, k = (int)nums.size() - 1;
            while(j < k){
                if(nums[j] + nums[k] == tempTarget){
                    res.push_back({nums[i], nums[j], nums[k]});
                    while(j < k && nums[j] == nums[j + 1]) j++;
                    while(j < k && nums[k] == nums[k - 1]) k--;
                    j++;
                    k--;
                }else if(nums[j] + nums[k] < tempTarget){
                    j++;
                }else{
                    k--;
                }
            }
        }
        return res;
    }
};
```

