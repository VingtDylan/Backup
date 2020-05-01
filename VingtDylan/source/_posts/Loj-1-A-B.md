---
title: Loj 1 A+B
mathjax: true
copyright: true
abbrlink: 1c57
date: 2020-05-01 11:09:26
tags:
  - Loj
  - Loj Test Problem
categories: Loj 
---

#### 题目描述

输入 $a$ 和 $b$，输出 $a$ + $b$ 的结果。

#### 输入格式

一行两个正整数 $a$ 和 $b$ 。

#### 输出格式

一行一个正整数$a$ + $b$。

<!--more-->

#### 样例

#### 样例输入

```
1 2
```

#### 样例输出

```
3
```

#### 数据范围与提示

对于100%的数据，1$\leq a,b \leq 10^6$。

#### AC代码

```c++
#include<bits/stdc++.h> 

int main(){
	int a,b;
	scanf("%d %d", &a, &b);
	printf("%d",a + b);
	return 0;
}
```

