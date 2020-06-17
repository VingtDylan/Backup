---
title: LeetCode 739
mathjax: true
copyright: true
tags:
  - LeetCode
  - 栈
  - 哈希表
categories: LeetCode
abbrlink: ad4b
date: 2020-06-11 00:04:08
---

#### [739. 每日温度](https://leetcode-cn.com/problems/daily-temperatures/)

难度: medium

根据每日 `气温` 列表，请重新生成一个列表，对应位置的输出是需要再等待多久温度才会升高超过该日的天数。如果之后都不会升高，请在该位置用 `0`来代替。

例如，给定一个列表 `temperatures = [73, 74, 75, 71, 69, 72, 76, 73]`，你的输出应该是 `[1, 1, 4, 2, 1, 1, 0, 0]`。

**提示：**`气温` 列表长度的范围是 `[1, 30000]`。每个气温的值的均为华氏度，都是在 `[30, 100]` 范围内的整数。

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/daily-temperatures
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```c++
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& T) {
        int len = T.size();
        vector<int> res(len, 0);
        stack<int> stk;
        for(int i = 0; i < len; i++){
            while(!stk.empty() && T[i] > T[stk.top()]){
                auto t = stk.top();stk.pop();
                res[t] = i - t;
            }
            stk.push(i);
        }
        return res;
    }
};
```

