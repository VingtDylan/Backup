---
title: LeetCode 136
mathjax: true
copyright: true
tags:
  - LeetCode
  - 位运算
  - 哈希表
categories: LeetCode
abbrlink: a8eb
date: 2020-05-14 00:04:35
---

#### [136. 只出现一次的数字](https://leetcode-cn.com/problems/single-number/)

难度: easy

给定一个**非空**整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

**说明：**

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

**示例 1:**

```
输入: [2,2,1]
输出: 1
```

<!--more-->

**示例 2:**

```
输入: [4,1,2,1,2]
输出: 4
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/single-number
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

至于其他思路哈希表啥的都很简单，懒得写了，因为没啥技术含量

```c++
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int res = 0;
        for(int num : nums)
            res ^= num;
        return res;
    }
};
```

