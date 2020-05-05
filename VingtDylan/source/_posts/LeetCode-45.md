---
title: LeetCode 45
mathjax: true
copyright: true
tags:
  - LeetCode
  - 贪心
categories: LeetCode
abbrlink: 382b
date: 2020-05-04 00:08:32
---

#### [45. 跳跃游戏 II](https://leetcode-cn.com/problems/jump-game-ii/)

难度: hard

给定一个非负整数数组，你最初位于数组的第一个位置。

数组中的每个元素代表你在该位置可以跳跃的最大长度。

你的目标是使用最少的跳跃次数到达数组的最后一个位置。

**示例:**

```
输入: [2,3,1,1,4]
输出: 2
解释: 跳到最后一个位置的最小跳跃数是 2。
     从下标为 0 跳到下标为 1 的位置，跳 1 步，然后跳 3 步到达数组的最后一个位置。
```

**说明:**

假设你总是可以到达数组的最后一个位置。

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/jump-game-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处

#### 思路

记录每一步活动范围内可以到达的新的活动范围，最小是走一步，最大时走nums[i] + i 步。

#### AC代码

```c++
class Solution {
public:
    int jump(vector<int>& nums) {
        if(nums.size() < 2)return 0;
        int n = (int)nums.size();
        int cur = 0, step = 0, last = 0;
        while(cur < n - 1){
            int fur = 0;
            for(int i = last; i <= cur; i++){
                fur = max(fur, nums[i] + i);
            }
            step++;
            last = cur + 1;cur = fur;
            if(cur >= n - 1)break;
        }
        return cur >= n - 1 ? step : -1;
    }
};
```

