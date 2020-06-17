---
title: LeetCode 1014
mathjax: true
copyright: true
tags:
  - LeetCode
  - 数组
categories: LeetCode
abbrlink: a81b
date: 2020-06-17 12:54:56
---

#### [1014. 最佳观光组合](https://leetcode-cn.com/problems/best-sightseeing-pair/)

难度: hard

给定正整数数组 `A`，`A[i]` 表示第 `i` 个观光景点的评分，并且两个景点 `i` 和 `j` 之间的距离为 `j - i`。

一对景点（`i < j`）组成的观光组合的得分为（`A[i] + A[j] + i - j`）：景点的评分之和**减去**它们两者之间的距离。

返回一对观光景点能取得的最高分。

**示例：**

```
输入：[8,1,5,2,6]
输出：11
解释：i = 0, j = 2, A[i] + A[j] + i - j = 8 + 5 + 0 - 2 = 11
```

**提示：**

1. `2 <= A.length <= 50000`
2. `1 <= A[i] <= 1000`

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/rotting-oranges
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    int maxScoreSightseeingPair(vector<int>& A) {
        int ans = 0;
        int aiplusi = A[0] + 0;
        for(int i = 1; i < A.size(); i++){
            ans = max(ans, aiplusi + A[i] - i);
            aiplusi = max(aiplusi, A[i] + i);
        } 
        return ans;
    }
};
```

