---
title: LeetCode 394
mathjax: true
copyright: true
tags:
  - LeetCOde
  - 深度优先搜索
  - 栈
categories: LeetCode
abbrlink: 9cd
date: 2020-05-28 00:25:56
---

#### [394. 字符串解码](https://leetcode-cn.com/problems/decode-string/)

难度: medium

给定一个经过编码的字符串，返回它解码后的字符串。

编码规则为: `k[encoded_string]`，表示其中方括号内部的 *encoded_string* 正好重复 *k* 次。注意 *k* 保证为正整数。

你可以认为输入字符串总是有效的；输入字符串中没有额外的空格，且输入的方括号总是符合格式要求的。

此外，你可以认为原始数据不包含数字，所有的数字只表示重复的次数 *k* ，例如不会出现像 `3a` 或 `2[4]` 的输入。

**示例:**

```
s = "3[a]2[bc]", 返回 "aaabcbc".
s = "3[a2[c]]", 返回 "accaccacc".
s = "2[abc]3[cd]ef", 返回 "abcabccdcdcdef".
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/decode-string
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    string decodeString(string s) {
        string t = "";
        stack<int> k;
        stack<string> str;
        int n = s.size();
        int count = 0;
        for(int i = 0; i < n; i++){
            if(s[i] >= '0' && s[i] <= '9'){
                count = 10 * count + s[i] - '0';
            }else if(s[i] == '['){
                k.push(count);
                str.push(t);
                count = 0;
                t.clear();
            }else if(s[i] == ']'){
                int num = k.top();
                k.pop();
                while(num--){
                    str.top() += t;
                }
                t = str.top();
                str.pop();
            }else{
                t += s[i];
            }
        }
        return str.empty() ? t : str.top();
    }
};
```

