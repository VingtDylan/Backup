---
title: LeetCode 221
mathjax: true
copyright: true
tags:
  - LeetCode
  - 动态规划
categories: LeetCode
abbrlink: fa5b
date: 2020-05-08 00:22:50
---

#### [221. 最大正方形](https://leetcode-cn.com/problems/maximal-square/)

难度: medium

在一个由 0 和 1 组成的二维矩阵内，找到只包含 1 的最大正方形，并返回其面积。

**示例:**

```
输入: 

1 0 1 0 0
1 0 1 1 1
1 1 1 1 1
1 0 0 1 0

输出: 4
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/maximal-square
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



#### AC 代码

```c++
class Solution {
public:
    int maximalSquare(vector<vector<char>>& matrix) {
        if(matrix.empty() || matrix[0].empty())return 0;
        int m = matrix.size();
        int n = matrix[0].size();
        vector<int> dp(m * n);
        int res = 0;
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(i == 0 || j == 0) dp[i * n + j] = matrix[i][j] - '0';
                else if(matrix[i][j] == '1'){
                    dp[i * n + j] = min(dp[i * n + j - 1], min(dp[(i - 1) *n + j - 1], dp[(i - 1) * n + j])) + 1; 
                }
                res = max(res, dp[i * n + j]);
            }
        }
        return res * res;
    }
};
```



#### 优化一下
好像优化的不咋样...

```c++
class Solution {
public:
    int maximalSquare(vector<vector<char>>& matrix) {
        if(matrix.empty() || matrix[0].empty())return 0;
        int m = matrix.size();
        int n = matrix[0].size();
        vector<int> dp(n + 1);
        int res = 0, pre = 0;
        for(int i = 0; i < m; i++){
            for(int j = 1; j <= n; j++){
                int temp = dp[j];
                if(matrix[i][j - 1] == '1'){
                    dp[j] = min(dp[j],min(dp[j - 1], pre)) + 1;
                    res = max(res, dp[j]);
                }else{
                    dp[j] = 0;
                }
                pre = temp;
            }
        }
        return res * res;
    }
};
```

