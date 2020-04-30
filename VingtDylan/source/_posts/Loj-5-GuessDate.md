---
title: Loj 5 GuessDate
mathjax: true
copyright: true
abbrlink: '0'
date: 2020-04-30 21:28:01
tags: Loj 数学 marked
categories: Loj测试题
---

#### 题目描述

给你一个提示，请猜测对应的日期。假设日期 x 用 1, 2, ..., n中的一个整数表示。

在任意一个数据点输出 0 都可以得到一定的同情分。

#### 输入格式

第一行一个整数 n ，表示日期 x 的范围是 1, 2, ..., n。

第二行一个字符串，为一个关于日期 x 的 Python 表达式，表示给出的提示。

#### 输出格式

对于每个测试点，请将对应答案写入 `date#.usr` 中，并填入网页下方提交答案处，或者以 zip 压缩包形式上传。

<!--less-->

#### 样例

#### 样例输入

```
10
abs(x - 7) == 4
```

#### 样例输出

```
3
```

#### 数据范围与提示

本题中给出的 Python 表达式与 C++ 语义相同。表达式中 `x` 是一个整型变量，当 `x` 为正确答案时，表达式求值为 `True`；否则为 `False`。保证答案惟一。

注：

- Python 中 `a ** b` 表示计算 $a^b$。
- `pi` 的值为 3.1415926535897932；三角函数使用弧度制。
- 给出的表达式可以直接在 Python 中 `from math import *` 后求值。
- 本题的测试数据中，`in` 文件是输出 0可得的分数百分比；`out` 文件是正确日期。在上传提交答案类题目时，如果 Special Judge 不需要 `in`/`out` 文件，可在 `data.yml` 中对应省略 `inputFile`/`outputFile` 项。
- **不保证** 答案是一个公历日期。



#### AC思路


#### date1.usr
题目:

```bash
1231
x * (x - 31) == 815184 - x
```

解方程，不bb

```c++
918
```

#### date2.usr

题目

```bash
20021231
(x ** x % 911) + (x ^ (x % 1248679)) == 20000000
```

我直接费马定理整一下，然后范围内暴力

```c++
20010911
for(long long i = 18750412; i <= 20021231 ;i++){
	long long t1 = i %  911, t2 = i % 910;
	long long res = 1;
	for(long long k = 1; k <= t2; k++){
		res = (res * t1) % 911;
	}
	long long m = i ^ (i % 1248679);
	if(res + m == 20000000){
		cout<<i<<endl;
		break;
	}
}
```

#### date3.usr

题目

```bash
1234567890
abs(2e9 - max(abs(x - 1e9), abs(x - 2e9), abs(x - 3e9))) <= 10 and abs(sin(pi * (x + 25) / 32)) <= 1e-8
```

不超过21个数字，暴力

```c++
1,000,000,007
const double pi = 3.141592653589793;
for(long long i = 1000000000 - 10; i <= 1000000000 + 10; i++){
	if(abs(sin(pi * (i + 25) / 32)) <= 1e-8){
		cout<<i<<endl;
		break;
	} 
	 
}
```
#### date4.usr

题目

```bash
1463030063184
x * ((x & -x) + ((x - (x & -x)) & -(x - (x & -x)))) == 1463030063184
```

好题,对lowbit进行枚举，代回去检验

```c++
121919171932

#define low(x) ((x) & (-x)) 
#define n 1463030063184
int m = log2(n);
long long lowx, lowy, t, x, tlowx, tlowy, s;
for(int i = 0; i <= m; i++){
	for(int j = 0; j <= m; j++){
		lowx = 2 << i;
		lowy = 2 << j;
		t = lowx + lowy;
		if(n % t)continue;
		x = n / t;
		tlowx = low(x);
		if(tlowx != lowx) continue;
		tlowy = low((x - tlowx));
		if(tlowy != lowy) continue;
		s = x * (tlowx + tlowy);
		if(s == n){
			cout<<x<<endl;
			break;
		}
	}
}
```

#### date5.usr

题目

```bash
1
not not not not not not not not x and not (((x + (x ^ 998244353) + (((((x + 123) % 456 * 789) ^ 987) - x * 654) ^ (321 * (x % 2))) - (987654321 ^ ((x * x) >> 1)) - (12344321 * x * x * x) - ((1234321 - x) ^ (123454321 >> 2) / (x - 12321) - ((x + (x * x * x) ^ (x * x)) / (x + 123))) * x + 456789 / (x + 9) + 87654 + (32 << (x + 1))) >> 19) + 1)

```

秒解

```c++
1
```



