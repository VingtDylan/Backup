---
title: LeetCode 315
mathjax: true
copyright: true
tags:
  - LeetCode
  - mark
  - 排序
  - 树状数组
  - 线段树
  - 二分查找
  - 分治算法
categories: LeetCode
abbrlink: 90b
date: 2020-07-18 14:47:36
---

#### [315. 计算右侧小于当前元素的个数](https://leetcode-cn.com/problems/count-of-smaller-numbers-after-self/)

难度: hard

给定一个整数数组 *nums*，按要求返回一个新数组 *counts*。数组 *counts*有该性质： `counts[i]` 的值是 `nums[i]` 右侧小于 `nums[i]` 的元素的数量。

**示例：**

```
输入：[5,2,6,1]
输出：[2,1,1,0] 
解释：
5 的右侧有 2 个更小的元素 (2 和 1)
2 的右侧仅有 1 个更小的元素 (1)
6 的右侧有 1 个更小的元素 (1)
1 的右侧有 0 个更小的元素
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/count-of-smaller-numbers-after-self/
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

```c++
class Solution {
public:
    vector<pair<int, int>> a;
    vector<pair<int, int>> b;
    vector<int> ans;
    vector<int> countSmaller(vector<int>& nums) {
        if (nums.empty()) return {};
        int n = nums.size();
        ans = vector<int>(n);
        b = vector<pair<int, int>> (n);
        for (int i = 0; i < n; i++) a.push_back({nums[i], i});
        merge_sort(a, 0, n - 1);
        return ans;
    }

    void merge_sort(vector<pair<int, int>>& a, int l, int r) {
        if (l == r) return;
        int mid = l + r >> 1;
        merge_sort(a, l, mid);
        merge_sort(a, mid + 1, r);
        int i = l, j = mid + 1, k = 0;
        while(i <= mid && j <= r){
            if (a[i].first <= a[j].first) {
                b[k++] = a[i];
                ans[a[i++].second] += j - mid - 1; 
            }
            else b[k++] = a[j++];
        }
        while (i <= mid) {
            ans[a[i].second] += r - mid; 
            b[k++] = a[i++];
        }
        while (j <= r) b[k++] = a[j++];
        for (int i = 0; i < k; i++) a[l + i] = b[i];
    }
};
```

