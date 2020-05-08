---
title: LeetCode 223
mathjax: true
copyright: true
tags:
  - LeetCode
  - 数学
categories: LeetCode
abbrlink: 3bda
date: 2020-05-08 01:08:45
---

#### [223. 矩形面积](https://leetcode-cn.com/problems/rectangle-area/)

难度: medium

在**二维**平面上计算出两个**由直线构成的**矩形重叠后形成的总面积。

每个矩形由其左下顶点和右上顶点坐标表示，如图所示。

![Rectangle Area](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/rectangle_area.png)

**示例:**

```
输入: -3, 0, 3, 4, 0, -1, 9, 2
输出: 45
```

**说明:** 假设矩形面积不会超出 **int** 的范围。

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/rectangle-area
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



#### AC代码

简单题...

```c++
class Solution {
public:
    int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
        int overlap;
        if(E >= C || G <= A || F >= D || H <= B){
            overlap = 0;
        }else{
            int x1 = max(A,E);
            int x2 = min(C,G);
            int y1 = max(B,F);
            int y2 = min(D,H);
            overlap = (x2 - x1) * (y2 - y1);
        }
        return (C - A) * (D - B) - overlap + (G - E) * (H - F);
    }
};
```

