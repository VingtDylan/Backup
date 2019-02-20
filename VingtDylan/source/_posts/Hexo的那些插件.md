---
title: Hexo的那些插件
mathjax: true
copyright: true
abbrlink: eeb6
date: 2019-02-20 16:59:59
tags:
  - Hexo插件
  - 博客优化
categories: Hexo
---

Hexo功能和优化等所需要的插件们....

原来搭建世界可以有那么多工具....

不如站在巨人的肩膀上看喽....

<!--less-->

1. pdf插件
- 安装插件
``` bash
npm install --save hexo-pdf
```
- 可以新增一个页面用来存放pdf
``` bash
hexo new page  pdf_Library
```
- 增添pdf的链接
可以在`source/pdf_Library`中找到`index.md`文件，编辑该文件:
```
1.外部链接
{ % pdf http://...... % }
2.内部(本地)链接
{ % pdf XXXX/XXX/.../*.pdf % }
```
2. maths类插件
3. 动画人物插件
4. ...