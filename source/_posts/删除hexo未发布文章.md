---
title: 删除hexo未发布文章
date: 2024-08-17 22:24:10
tags: hexo
categories: 教程
---

普通删除方式
Hexo正常删除文章的流程是先删除本地文件。

以原始文件：helloworld.md为例：

首先进入到source / _post 文件夹中，找到helloworld.md文件，在本地直接执行删除。

然后依次执行命令：

```
hexo clean
```
```
hexo g
```
```
hexo d
```
此时已经成功删除文章了。

转自
```
https://www.yuezeyi.com/294.html
```
