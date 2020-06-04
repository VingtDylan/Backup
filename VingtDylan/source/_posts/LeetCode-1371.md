---
title: LeetCode 1371
mathjax: true
copyright: true
tags:
  - LeetCode
  - 字符串
  - 前缀和
  - 状态压缩
  - mark
categories: LeetCode
abbrlink: b28
date: 2020-05-20 21:06:54
---

#### [1371. 每个元音包含偶数次的最长子字符串](https://leetcode-cn.com/problems/find-the-longest-substring-containing-vowels-in-even-counts/)

难度: medium

给你一个字符串 `s` ，请你返回满足以下条件的最长子字符串的长度：每个元音字母，即 'a'，'e'，'i'，'o'，'u' ，在子字符串中都恰好出现了偶数次。

**示例 1：**

```
输入：s = "eleetminicoworoep"
输出：13
解释：最长子字符串是 "leetminicowor" ，它包含 e，i，o 各 2 个，以及 0 个 a，u 。
```

<!--more-->

**示例 2：**

```
输入：s = "leetcodeisgreat"
输出：5
解释：最长子字符串是 "leetc" ，其中包含 2 个 e 。
```

**示例 3：**

```
输入：s = "bcbcbc"
输出：6
解释：这个示例中，字符串 "bcbcbc" 本身就是最长的，因为所有的元音 a，e，i，o，u 都出现了 0 次。
```

**提示：**

- `1 <= s.length <= 5 x 10^5`
- `s` 只包含小写英文字母。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/divisor-game
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    int findTheLongestSubstring(string s) {
        int res = 0, flag = 0;
        vector<int> position(32, -1);
        position[0] = 0;
        for(int i = 0; i < s.size(); i++){
            char c = s[i];
            switch(c){
                case 'a': flag ^= 1 << 0; break;
                case 'e': flag ^= 1 << 1; break;
                case 'i': flag ^= 1 << 2; break;
                case 'o': flag ^= 1 << 3; break;
                case 'u': flag ^= 1 << 4; break;
                default:break;
            }
            if(position[flag] == -1){
                position[flag] = i + 1;
            }else{
                res = max(res, i - position[flag] + 1);
            }
        }
        return res;
    }
};
```
