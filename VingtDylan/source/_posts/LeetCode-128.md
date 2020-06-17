---
title: LeetCode 128
mathjax: true
copyright: true
tags:
  - LeetCode
  - 并查集
  - 数组
  - mark
categories: LeetCode
abbrlink: fc6b
date: 2020-06-06 17:26:19
---

#### [128. 最长连续序列](https://leetcode-cn.com/problems/longest-consecutive-sequence/)

难度: hard

给定一个未排序的整数数组，找出最长连续序列的长度。

要求算法的时间复杂度为 *O(n)*。

**示例:**

```
输入: [100, 4, 200, 1, 3, 2]
输出: 4
解释: 最长连续序列是 [1, 2, 3, 4]。它的长度为 4。
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/longest-consecutive-sequence
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

时间消耗还是挺大的。。。

```c++
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_map<int,int> a;
        for(auto num : nums){
            a[num] = num;
        }
        int res = 0;
        int len = nums.size() - 1;
        for(int i = len; i >= 0; i--){
            if(!a.count(nums[i] - 1)){
                int cur = nums[i];
                int t = 1;
                while(a.count(cur + 1)){
                    cur++;
                    t++;
                }
                res =  max(res, t);
            }
        }
        return res;
    }
};
```

