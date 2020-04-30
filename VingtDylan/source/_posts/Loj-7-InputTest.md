---
title: Loj 7 InputTest
mathjax: true
copyright: true
abbrlink: f7ec
date: 2020-04-30 21:28:33
tags: Loj 
categories: Loj测试题
---

#### 题目描述

输入 $3\times 10^6$个$[0,2^m)$中均匀随机的十进制整数，输出它们的异或和。

#### 输入格式

输入共 $3\times 10^6$ 行，每行一个整数。

#### 输出格式

输出共一行一个整数表示它们的异或和。

#### 数据范围与提示

共5组数据， 分别为 1, 3, 15, 31, 63 。

<!--less-->

#### AC代码

```c++
#include<iostream>
using namespace std;
int main(){
    long long res = 0;
    long long c =3 * 1000000;
    long long a;
    while(c--){
        cin>>a;
        res ^= a;
    }
    cout<<res<<endl;
    return 0;
}
```

