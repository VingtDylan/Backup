---
title: LeetCode 14
mathjax: true
copyright: true
tags:
  - LeetCode
  - 字符串
categories: LeetCode
abbrlink: a8e9
date: 2020-06-15 16:58:28
---

#### [14. 最长公共前缀](https://leetcode-cn.com/problems/longest-common-prefix/)

难度: easy 

编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 `""`。

**示例 1:**

```
输入: ["flower","flow","flight"]
输出: "fl"
```

<!--more-->

**示例 2:**

```
输入: ["dog","racecar","car"]
输出: ""
解释: 输入不存在公共前缀。
```

**说明:**

所有输入只包含小写字母 `a-z` 。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/longest-common-prefix
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

####  AC代码

```c++
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if(strs.empty())return "";
        sort(strs.begin(),strs.end());
        int len = min(strs[0].size(),strs.back().size());
        int i = 0;
        while(i < len && strs[0][i] == strs.back()[i])i++;
        return strs[0].substr(0,i);
    }
};
```

