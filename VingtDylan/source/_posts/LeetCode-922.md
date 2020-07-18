---
title: LeetCode 922
mathjax: true
copyright: true
tags:
  - LeetCode
  - 排序
  - 数组
categories: LeetCode
abbrlink: 396a
date: 2020-07-18 14:47:49
---

#### [922. 按奇偶排序数组 II](https://leetcode-cn.com/problems/sort-array-by-parity-ii/)

难度: easy

给定一个非负整数数组 `A`， A 中一半整数是奇数，一半整数是偶数。

对数组进行排序，以便当 `A[i]` 为奇数时，`i` 也是奇数；当 `A[i]` 为偶数时， `i` 也是偶数。

你可以返回任何满足上述条件的数组作为答案。

**示例：**

```
输入：[4,2,5,7]
输出：[4,5,2,7]
解释：[4,7,2,5]，[2,5,4,7]，[2,7,4,5] 也会被接受。
```

**提示：**

1. `2 <= A.length <= 20000`
2. `A.length % 2 == 0`
3. `0 <= A[i] <= 1000`

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/sort-array-by-parity-ii/
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    vector<int> sortArrayByParityII(vector<int>& A) {
        int odd = 1, even = 0;
        for(int even = 0; even < A.size(); even += 2){
            if(A[even] & 1){
                while(A[odd] & 1)odd += 2;
                swap(A[odd],A[even]);
            }
        }
        return A;
    }
};
```

