---
title: LeetCode 32
mathjax: true
copyright: true
tags:
  - LeetCode
  - 字符串
  - 动态规划
categories: LeetCode
abbrlink: ca68
date: 2020-07-04 00:13:02
---

#### [32. 最长有效括号](https://leetcode-cn.com/problems/longest-valid-parentheses/)

难度: hard

给定一个只包含 `'('` 和 `')'` 的字符串，找出最长的包含有效括号的子串的长度。

**示例 1:**

```
输入: "(()"
输出: 2
解释: 最长有效括号子串为 "()"
```

**示例 2:**

```
输入: ")()())"
输出: 4
解释: 最长有效括号子串为 "()()"
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/longest-valid-parentheses
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

子串$\neq$字序列

```c++
class Solution {
public:
    int longestValidParentheses(string s) {
        int sum = 0;
        s = ')' + s;
        vector<int> dp(s.length(),0);
        for(int i = 1; i < s.length(); i++){
            if(s[i] == ')'){
                if(s[i - 1 - dp[i-1]] == '('){
                    dp[i] = dp[i-1] + 2;
                    dp[i] += dp[i - dp[i]];
                }
            }
            sum = max(sum,dp[i]);
        }
        return sum;
    }
};
```