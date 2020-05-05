---
title: LeetCode 3
mathjax: true
copyright: true
tags:
  - LeetCode
  - 哈希表
  - 双指针
  - sliding window
categories: LeetCode
abbrlink: a92b
date: 2020-05-02 01:55:32
---

#### [3. 无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

难度: medium

给定一个字符串，请你找出其中不含有重复字符的 **最长子串** 的长度。

**示例 1:**

```
输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

<!--more-->

**示例 2:**

```
输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```

**示例 3:**

```
输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/longest-substring-without-repeating-characters
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### 思路

hash记录字符的索引，size = i - left，left表示当前不重复的子串的最左元素的索引

#### AC代码

```c++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        vector<int> vec(128, -1);
        int res = 0, left = -1;
        for(int i = 0; i < s.size(); i++){
            left = max(left, vec[s[i]]);
            vec[s[i]] = i;
            res = max(res, i - left);
        }
        return res;
    }
};
```



