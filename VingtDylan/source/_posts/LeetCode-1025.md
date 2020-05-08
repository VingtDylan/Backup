---
title: LeetCode 1025
mathjax: true
copyright: true
tags:
  - LeetCode
  - 数学
  - 动态规划
categories: LeetCode
abbrlink: 98da
date: 2020-05-08 22:15:17
---

#### [1025. 除数博弈](https://leetcode-cn.com/problems/divisor-game/)

难度:  easy

爱丽丝和鲍勃一起玩游戏，他们轮流行动。爱丽丝先手开局。

最初，黑板上有一个数字 `N` 。在每个玩家的回合，玩家需要执行以下操作：

- 选出任一 `x`，满足 `0 < x < N` 且 `N % x == 0` 。
- 用 `N - x` 替换黑板上的数字 `N` 。

如果玩家无法执行这些操作，就会输掉游戏。

只有在爱丽丝在游戏中取得胜利时才返回 `True`，否则返回 `false`。假设两个玩家都以最佳状态参与游戏。

**示例 1：**

```
输入：2
输出：true
解释：爱丽丝选择 1，鲍勃无法进行操作。
```

<!--more-->

**示例 2：**

```
输入：3
输出：false
解释：爱丽丝选择 1，鲍勃也选择 1，然后爱丽丝无法进行操作。
```

**提示：**

1. `1 <= N <= 1000`

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/divisor-game
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

常规动态规划

```c++
class Solution {
public:
    bool divisorGame(int N) {
        if(N < 2)return false;
        vector<int> dp(N + 1);
        dp[1] = false;dp[2] = true;
        for(int i = 3; i <= N; i++){
            dp[i] = false;
            for(int j = 1; j < i; j++){
                if(i % j)continue;
                else{
                    if(!dp[i - j]){
                        dp[i] = true;
                        break;
                    }
                }
            }
        }
        return dp[N];
    }
};
```

#### 优化一下

1->false

2->true

3->false

4->true(4,3,2->false)

猜想:奇数->false;偶数->true

证明: $dp[2k-1] = false, dp[2k] = true$

$k = 1$时，显然成立

假设$k \leq m$时，成立

则$k\leq m + 1$时，显然  $(2*m+1) \% x = 0 \rightarrow x = 2*n + 1$$dp[2*m+ 1] = !dp[2*m +1 - x] = !dp[2 * n] = false$

$dp[2*m + 1] = !dp[2*m + 2 - 1] = !dp[2*m + 1] = true$成立

```c++
class Solution {
public:
    bool divisorGame(int N) {
        return N % 2 == 0;
    }
};
```