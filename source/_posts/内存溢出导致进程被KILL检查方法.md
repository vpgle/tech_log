---
title: 内存溢出导致进程被KILL检查方法
date: 2024-09-01 20:42:26
tags:
categories: linux
---

用demsg -T | grep -i -E -B100 "killed process"
输出内容有进程号，可以进行比对
