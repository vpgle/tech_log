---
title: window wmic
date: 2024-09-09 21:50:02
tags:
categories: window
---


window下通过进程ID查询进程所在路径

wmic process get name,executablepath,processid | findstr pid

