---
title: Markdown学习1
tags:
  - Markdown
  - 语法
categories: Markdown
abbrlink: ffd7
date: 2019-02-18 01:04:42
copyright: true
---

### 标题
在Markdown中，只需要在文本前面加入`#`即可设置标题格式，同理，可以设置二级，三级，四级，五级和六级标题，只需增加`#`的个数，标题的字号将会相应的降低。如下所示:
```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```
注:`#`和`[一级标题]`之间建议保留一个空格，这是最标准的Markdown写法。(以防出错)

<!--less-->

### 列表
在Markdown中只需要在文字的前面加上`-`即可，如下所示:
```
- 文本1
- 文本2
- 文本3
```
如果希望获得一个有序列表，只需修改为`1.` `2.` `3.`即可，如下所示:
```
1. 文本1
2. 文本2
3. 文本3
```
注:`-`、`1.`和文本之间需要保留一个字符的空格。

<!-- <h2 id="picture">链接和图片</h2> -->
### 链接和图片
在Markdown中，插入链接不需要其他按钮，只需要使用`[显示文本](链接地址)`这样即可，例如:`[爸爸的博客](https://vingtdylan.github.io/)`
效果如下:
[爸爸的博客](https://vingtdylan.github.io/)

类似的，在Markdown中，插入图片不需要其他按钮，只需要使用`![](链接地址)`这样即可，例如:
`![](https://vingtdylan.github.io)`
效果如下:
![](http://upload-images.jianshu.io/upload_images/259-0ad0d0bfc1c608b6.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 引用
在写作的时候经常需要引用他人的文字，这时候需要添加引用格式，在Markdown中，只需添加一个`>`即可，例如:`>那些年你冒险的梦`
注:`>`和文本之间仍需要一个字符的空格
效果如下:
>那些年你冒险的梦

### 粗体和斜体
Markdown中的粗体和斜体只需要用`*`或者`**`将文本包含起来即可，例如:
`**那些年**你很*冒险的梦*`
效果如下:
**那些年**你很*冒险的梦*

### 代码引用
当行使用(\`)将语句包起来，如果引用多行语句，则用(\`\`\`)包含文本即可，例如
`` `hello world` ``
和
`` ` ` ` ``
`` `#include<iostream>` ``
`` `using namespace std` ``
`` `int main(){}` ``
`` ` ` ` ``
显示效果依次为:
`hello world`
```
#include<iostream>
using namespace std;
int main(){}
```
特别提示，在代码块中打出```` ``` ````需要用4个`` ` ``包含3个`` ` ``.

### 表格
```
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
```
显示效果为:

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

注:表格上方必须为一个空行

### 显示链接中带括号的图片
```
![][1]
[1]: http://latex.codecogs.com/gif.latex?\prod%20(n_{i})+1
```
显示效果为:
![][1]
[1]: http://latex.codecogs.com/gif.latex?\prod%20(n_{i})+1
`Hexo中显示有问题...`





