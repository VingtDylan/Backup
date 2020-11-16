---
title: LeetCode 406
mathjax: true
copyright: true
tags:
  - LeetCode
  - 贪心
categories:
  - LeetCode
abbrlink: 59fb
date: 2020-11-16 15:56:27
---

#### [406. 根据身高重建队列](https://leetcode-cn.com/problems/queue-reconstruction-by-height/)

难度: medium

假设有打乱顺序的一群人站成一个队列。 每个人由一个整数对`(h, k)`表示，其中`h`是这个人的身高，`k`是排在这个人前面且身高大于或等于`h`的人数。 编写一个算法来重建这个队列。

**注意：**
总人数少于1100人。

**示例**

```
输入:
[[7,0], [4,4], [7,1], [5,0], [6,1], [5,2]]

输出:
[[5,0], [7,0], [5,2], [6,1], [4,4], [7,1]]
```

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/queue-reconstruction-by-height
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

**AC代码**

从高到矮，次序从小到大排序

根据次序insert

```c++
class Solution {
public:
    vector<vector<int>> reconstructQueue(vector<vector<int>>& people) {
        vector<vector<int>> res;
        sort(people.begin(),people.end(),[&](vector<int> a,vector<int> b){
            return a[0] > b[0] || (a[0] == b[0] && a[1] < b[1]);
        });
        //for(auto p : people)cout<<p[0]<<p[1]<<endl;
        for(auto p : people)res.insert(res.begin() + p[1], p);
        return res;
    }
};
```

