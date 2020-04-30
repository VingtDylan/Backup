---
title: Loj 1 A+B
mathjax: true
copyright: true
tags: Loj
categories: Loj测试题
abbrlink: 1c57
date: 2020-04-30 21:19:37
---

#### 题目描述

输入 $a$和$b$，输出 $a$ + $b$的结果。

#### 输入格式

一行两个正整数$a$和$b$ 。

#### 输出格式

一行一个正整数$a$ + $b$。

<!--less-->

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

