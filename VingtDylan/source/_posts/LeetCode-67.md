---
title: LeetCode 67
mathjax: true
copyright: true
tags:
  - LeetCode
  - 字符串
  - 数字
categories: LeetCode
abbrlink: 99ab
date: 2020-06-23 12:44:41
---

#### [67. 二进制求和](https://leetcode-cn.com/problems/add-binary/)

难度: easy

给你两个二进制字符串，返回它们的和（用二进制表示）。

输入为 **非空** 字符串且只包含数字 `1` 和 `0`。

**示例 1:**

```
输入: a = "11", b = "1"
输出: "100"
```

<!--more-->

**示例 2:**

```
输入: a = "1010", b = "1011"
输出: "10101"
```

**提示：**

- 每个字符串仅由字符 `'0'` 或 `'1'` 组成。
- `1 <= a.length, b.length <= 10^4`
- 字符串如果不是 `"0"` ，就都不含前导零。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/add-binary
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    string addBinary(string a, string b) {
        string res = "";
        int alen = a.size() - 1;
        int blen = b.size() - 1;
        int carry = 0;
        while(alen >= 0 || blen >= 0){
            int as = alen >= 0 ? a[alen--] - '0' : 0;
            int bs = blen >= 0 ? b[blen--] - '0' : 0;
            int s = as + bs + carry;
            res = to_string(s % 2) + res;
            carry =  s / 2;
        }
        return carry > 0 ? '1' + res : res;
    }
};
```

