---
title: LeetCode 125
mathjax: true
copyright: true
tags:
  - LeetCode
  - 双指针
  - 字符串
categories: LeetCode
abbrlink: 39aa
date: 2020-06-19 00:10:58
---

#### [125. 验证回文串](https://leetcode-cn.com/problems/valid-palindrome/)

难度: easy

给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。

**说明：**本题中，我们将空字符串定义为有效的回文串。

**示例 1:**

```
输入: "A man, a plan, a canal: Panama"
输出: true
```

<!--more-->

**示例 2:**

```
输入: "race a car"
输出: false
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/valid-palindrome
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    bool isPalindrome(string s) {
        string temp = "";
        for(char c : s){
            if(valid(c)){
                temp += c;
            }
        }
        if(temp.size() <= 1)return true;
        int l = 0, r = temp.size() - 1;
        while(l < r){
            if(tolower(temp[l]) != tolower(temp[r]))
                return false;
            l++;
            r--;
        }
        return true;
    }
    bool valid(char c){
        if(c >= '0' && c <= '9')return true;
        if(c >= 'a' && c <= 'z')return true;
        if(c >= 'A' && c <= 'Z')return true;
        return false;
    }
};
```

