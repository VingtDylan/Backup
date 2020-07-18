---
title: LeetCode 97
mathjax: true
copyright: true
tags:
  - LeetCode
  - 字符串
  - 动态规划
  - mark
categories: LeetCode
abbrlink: 69ae
date: 2020-07-18 15:15:07
---

#### [97. 交错字符串](https://leetcode-cn.com/problems/interleaving-string/)

难度: hard

给定三个字符串 *s1*, *s2*, *s3*, 验证 *s3* 是否是由 *s1* 和 *s2* 交错组成的。

**示例 1:**

```
输入: s1 = "aabcc", s2 = "dbbca", s3 = "aadbbcbcac"
输出: true
```

**示例 2:**

```
输入: s1 = "aabcc", s2 = "dbbca", s3 = "aadbbbaccc"
输出: false
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/interleaving-string/
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    bool isInterleave(string s1, string s2, string s3) {
        int s1_size = s1.size();
        int s2_size = s2.size();
        int s3_size = s3.size();
        if(s1_size + s2_size != s3_size)return false;
        vector<bool> f(s2_size + 1, false);
        f[0] = true;
        for(int i = 0; i <= s1_size; i++){
            for(int j = 0; j <= s2_size; j++){
                int p = i + j - 1;
                if(i > 0)f[j] = f[j] & (s1[i - 1] == s3[p]);
                if(j > 0)f[j] = f[j] | (f[j - 1] && s2[j - 1] == s3[p]); 
            }
        }
        return f[s2_size];
    }
};
```

