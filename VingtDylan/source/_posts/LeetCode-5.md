---
title: LeetCode 5
mathjax: true
copyright: true
tags:
  - LeetCode
  - 字符串
  - 动态规划
  - 马拉车算法
  - mark
categories: LeetCode
abbrlink: abab
date: 2020-05-21 11:56:53
---

#### [5. 最长回文子串](https://leetcode-cn.com/problems/longest-palindromic-substring/)

难度: medium

给定一个字符串 `s`，找到 `s` 中最长的回文子串。你可以假设 `s` 的最大长度为 1000。

**示例 1：**

```
输入: "babad"
输出: "bab"
注意: "aba" 也是一个有效答案。
```

<!--more-->

**示例 2：**

```
输入: "cbbd"
输出: "bb"
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/longest-palindromic-substring
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

####  AC代码

##### 动态规划

````c++
class Solution {
public:
    string longestPalindrome(string s) {
        if(s.empty())return "";
        int n = s.size();
        vector<vector<int>> dp(n, vector<int>(n, 0));
        int len = 1, st = 0;
        for(int i = 0; i < n; i++){
            dp[i][i] = 1;
            for(int j = 0; j < i; j++){
                dp[j][i] = (s[j] == s[i]) && (i - j < 2 || dp[j + 1][i - 1]);
                if(dp[j][i] && len < i - j + 1){
                    len = i - j + 1;
                    st = j;
                }
            }
        }
        return s.substr(st, len);
    }
};
````

##### 马拉车算法(Manacher's Algorithm)

参考[马拉车算法](https://www.jianshu.com/p/392172762e55)

```c++
class Solution {
public:
    string longestPalindrome(string s) {
        string newS = "$#";
        for(char c : s){
            newS += c;
            newS += '#';
        }
        newS += '@';
        int n = newS.size();
        vector<int> p(n);
        int id = 0, mx = 0;
        int len = 1, idx = 0;
        for(int j = 1; j < n - 1; j++){
            p[j] = mx > j ? min(p[2 * id - j], mx - j) : 1;
            while(newS[j + p[j]] == newS[j - p[j]])p[j]++;
            if(mx < p[j] + j){
                mx = p[j] + j;
                id = j;
            }
            if(len < p[j] - 1){
                len = p[j] - 1;
                idx = j;
            }
        }
        int st = (idx - len) / 2;
        return s.substr(st, len);
    }
};
```



