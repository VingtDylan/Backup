---
title: Loj 3 Copycat
mathjax: true
copyright: true
abbrlink: 671d
date: 2020-05-01 11:14:09
tags: 
  - Loj
  - Loj Test Problem
categories: Loj 
---

#### 题目描述

这道题用于测试文件输入输出，**请注意使用文件输入输出，而非标准输入输出。**

输入一个正整数 $a$，输出这个数 $a$。

#### 输入格式

第一行一个 $T$ 正整数 ，表示有 $T$ 组测试数据。
接下来 $T$ 行，每行一个正整数 $a$ 。

#### 输出格式

输出$T$行，每行一个正整数$a$。

<!--more-->

#### 样例

#### 样例输入 1

```
3
1
2
3
```

#### 样例输出 1

```
1
2
3
```

#### 样例输入 2

```
1
1000000000000000000000000000000000
```

#### 样例输出 2

```
1000000000000000000000000000000000
```

#### 数据范围与提示

对于所有测试点，$1\leq T \leq 10, 1 \leq a \leq 10^{1000}$。

**子任务 1**（10 分）$1\leq a \leq 3$；
**子任务 2**（20 分）$1\leq a \leq 100000$；
**子任务 3**（70 分）没有附加限制。



#### AC代码

```c++
#include<bits/stdc++.h>

using namespace std;

int main(){
	freopen("copycat.in","r",stdin);
	freopen("copycat.out","w",stdout);
	int T;cin>>T;
	string a;
	while(T--){
		cin>>a;
		cout<<a<<endl;
	}
	return 0;
}
```

