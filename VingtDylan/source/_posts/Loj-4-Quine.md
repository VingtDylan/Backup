---
title: Loj 4 Quine
mathjax: true
copyright: true
tags: 
  - Loj 
  - mark
  - Loj Test Problem
categories: Loj
abbrlink: '9124'
date: 2020-05-01 11:18:03
---

#### 题目描述

写一个程序，使其能输出自己的源代码。

代码中必须至少包含十个可见字符。

#### 输入格式

输入文件为空。

#### 输出格式

你的源代码。

<!--more-->

这是一个有趣的问题，Google一下

#### AC代码

```c++
#include <stdio.h>

char *s = "#include <stdio.h>%c%cchar *s = %c%s%c;%c%cint main(){%c%c%c%c%cprintf(s,10,10,34,s,34,10,10,10,32,32,32,32,10,10);%c}%c";

int main(){
    printf(s,10,10,34,s,34,10,10,10,32,32,32,32,10,10);
}
```

