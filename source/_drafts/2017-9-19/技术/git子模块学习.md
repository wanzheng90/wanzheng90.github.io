---
title: git子模块学习
date: 2016-09-27 11:29:56
tags: git
---

# git子模块简介
git 子模块主要作用是在代码中引用其他git项目
<!---more--->

# 用法

## 新增子模块
``` git
git submodule add git仓库地址 子模块存放目录
```

## 初始化子模块
若下载项目中包含子模块，在clone项目时并不会包含子模块，执行下面两条命令来clone子模块

```git
git submodule init
git submodule update
```
