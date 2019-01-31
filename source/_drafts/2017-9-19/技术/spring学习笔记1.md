---
title: spring学习笔记1(整体介绍)
date: 2017-03-25 20:17:47
tags: java,spring
---

# spring 整体架构
![spring整体架构](/pic/spring-runtime.png)

# 模块介绍
spring-core:核心工具类，被其它spring模块使用。封装了线程、io、类等操作。
spring-beans:bean支持类。和spring-core构成了整个spring框架的基础，提供了控制反转和依赖注入功能。
spring-context:提供运行时上下文，包括调度器和远程抽象
spring-expression:spring表达式语言
spring-aop:基于代理的面向切面编程
spring-aspects:基于AspectJ切面实现
待续。。。
