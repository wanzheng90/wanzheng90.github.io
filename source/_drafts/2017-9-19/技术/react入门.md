---
title: react入门
date: 2017-02-06 17:53:48
tags: react
---

react 是Facebook推出的非常流行的一个前端组件化库，当前github上star超过5万。

<!--more-->

## react要解决的问题是什么？
react主要解决前端组件化问题

## 为何前端要解决组件化问题？
组件化是对html、css、js的抽象封装。当页面规模很大时，如果不进行组件化，html、css、js相互影响会导致页面最终失控，使用组件化将html、css、js抽象为一个组件单元后，可以明确作用域，减少耦合。同时将页面模块抽象后可以提出共性，便于复用。

## 前端组件化框架有很多（vue、angular），react有何优势？
1、react以js为核心（all in js），react以前的框架核心还是以模板+数据为主（当然现在其它框架也都吸收了相关的特性）。以dom结构模板为主对界面设计更友好，以js为主则对程序员更友好，运用编程思想来解决UI问题，毕竟程序员并不擅长调样式；
2、react将整个视图视为状态机ui=f(state)，状态变更时重新渲染整个UI，副作用小,结合flux框架，统一管理状态，状态更清晰。mvvm框架一个问题就是容易造成状态分散在各个组件中,规模大之后难以维护。但flux框架也导致代码量大大增加。

# 示例

## 安装react cli工具
react依赖项目太多（webpack、babel）且配置项繁杂，为快速入门，先安装react 项目生成工具
```
npm install -g create-react-app
```

## 生成项目并运行
```
create-react-app my-app
cd my-app/
npm start
```
打开 http://localhost:3000/ 即可看到项目运行结果
