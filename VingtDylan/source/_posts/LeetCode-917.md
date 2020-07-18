---
title: LeetCode 917
mathjax: true
copyright: true
tags:
  - LeetCode
  - 字符串
categories: LeetCode
abbrlink: caaa
date: 2020-07-18 14:47:56
---

#### [917. 仅仅反转字母](https://leetcode-cn.com/problems/reverse-only-letters/)

难度: easy

给定一个字符串 `S`，返回 “反转后的” 字符串，其中不是字母的字符都保留在原地，而所有字母的位置发生反转。

**示例 1：**

```
输入："ab-cd"
输出："dc-ba"
```

**示例 2：**

```
输入："a-bC-dEf-ghIj"
输出："j-Ih-gfE-dCba"
```

**示例 3：**

```
输入："Test1ng-Leet=code-Q!"
输出："Qedo1ct-eeLg=ntse-T!"
```

**提示：**

1. `S.length <= 100`
2. `33 <= S[i].ASCIIcode <= 122` 
3. `S` 中不包含 `\` or `"`

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/reverse-only-letters/
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    string reverseOnlyLetters(string S) {
        int l = 0, r = S.size() - 1;
        while(l < r){
            while(!isalpha(S[l]) && l < r)l++;
            while(!isalpha(S[r]) && l < r)r--;
            if(l < r){
                swap(S[l],S[r]);
                l++,r--;
            }
        }
        return S;
    }
};
```

