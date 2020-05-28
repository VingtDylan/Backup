---
title: LeetCode 974
mathjax: true
copyright: true
tags:
  - LeetCode
  - 数组
  - 哈希表
categories: LeetCode
abbrlink: 6be9
date: 2020-05-27 00:03:47
---

#### [974. 和可被 K 整除的子数组](https://leetcode-cn.com/problems/subarray-sums-divisible-by-k/)

难度: medium

给定一个整数数组 `A`，返回其中元素之和可被 `K` 整除的（连续、非空）子数组的数目。

**示例：**

```
输入：A = [4,5,0,-2,-3,1], K = 5
输出：7
解释：
有 7 个子数组满足其元素之和可被 K = 5 整除：
[4, 5, 0, -2, -3, 1], [5], [5, 0], [5, 0, -2, -3], [0], [0, -2, -3], [-2, -3]
```

**提示：**

1. `1 <= A.length <= 30000`
2. `-10000 <= A[i] <= 10000`
3. `2 <= K <= 10000`

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/subarray-sums-divisible-by-k
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

果然低端前缀和走不远，跟[LeetCode 560](https://vingtdylan.github.io/p/3b29.html)差不多，注意负数的问题就是了

这就是同余的力量吧

```c++
class Solution {
public:
    int subarraysDivByK(vector<int>& A, int K) {
        /*TLE
        int n = A.size();
        vector<int> dp(n + 1);
        for(int i = 1; i < n + 1; i++){
            dp[i] = dp[i - 1] + A[i - 1];
        }
        int res = 0;
        for(int i = 1; i < dp.size(); i++){
            for(int j = 0; j < i; j++){
                if((dp[j] - dp[i]) % K == 0){
                    res++;
                }
            }
        }
        return res;
        */
        int res = 0, sum = 0, n = A.size();
        unordered_map<int,int> mp{{0,1}};
        for(int i = 0; i < n; i++){
            sum += (A[i] % K + K) % K;
            sum %= K;
            res += mp[sum];
            mp[sum]++;
        }
        return res;
    }
};
```

