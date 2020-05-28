---
title: LeetCode 76
mathjax: true
copyright: true
tags:
  - LeetCode
  - 哈希表
  - 双指针
  - 字符串
  - Sliding Window
  - mark
categories: LeetCode
abbrlink: c96b
date: 2020-05-23 00:07:12
---

#### [76. 最小覆盖子串](https://leetcode-cn.com/problems/minimum-window-substring/)

难度: hard

给你一个字符串 S、一个字符串 T，请在字符串 S 里面找出：包含 T 所有字符的最小子串。

**示例：**

```
输入: S = "ADOBECODEBANC", T = "ABC"
输出: "BANC"
```

**说明：**

- 如果 S 中不存这样的子串，则返回空字符串 `""`。
- 如果 S 中存在这样的子串，我们保证它是唯一的答案。

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/minimum-window-substring
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    string minWindow(string s, string t) {
        unordered_map<char,int> mp;
        for(char c : t)mp[c]++;
        int len = s.size(), target = t.size();
        int count = 0, left = 0;
        int length = INT_MAX, minleft = -1;
        for(int i = 0; i < len; i++){
            if(--mp[s[i]] >= 0){
                count++;
            }
            while(count == target){
                int temp = i - left + 1;
                if(temp < length){
                    length = temp;
                    minleft = left;
                }
                if(++mp[s[left]] > 0)count--;
                left++;
            }
        }
        return minleft == -1 ? "" : s.substr(minleft,length);
    }
};
```

