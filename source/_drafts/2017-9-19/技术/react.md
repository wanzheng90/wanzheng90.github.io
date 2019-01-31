---
title: react
date: 2017-01-04 15:58:57
tags: react
---
# 简介

react 是有Facebook发布的前端js框架，专注于vue层，让界面可以进行组件化开发。



<!--more-->

# 特点

1、底层采用虚拟dom技术

2、在js中混入xml代码

3、每次修改数据都会生存整个界面dom结构，框架会在底层对比新老dom之间的区别，然后更新有变更的部分

4、将界面组件化



# 优点

1、由于采用虚拟dom，与底层具体实现隔离，可以让跨平台开发（react-native）。learn once, write anywhere

2、让界面组建化,提高复用性和分解开发难度

3、jsx文件将xml与js合并在一起，结合了xml结构化容易描述页面优点与js图灵完备的优点，不用在xml中再定义循环、判断语句



# 缺点

1、all in js与w3c规范不兼容

2、将xml于js混在一起，容易让代码不易阅读
