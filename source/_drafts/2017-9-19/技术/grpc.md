---
title: grpc
date: 2017-01-04 17:51:38
tags: grpc
---
# 简介

grpc是google推出的rpc开源框架。在docker、kubernet中均有用到

<!--more-->

# 特点

1、传输层基于http2

2、数据编码采用protobuf文件

3、接口定义采用自定义dsl

# 优点

1、基于http2。可以透明的使用http代理，实现负载均衡

2、可以实现链路复用，不用每次请求都发起新的连接

3、采用protobuf文件编码，使传输数据变小

4、能够实现跨语言调用，主流语言（c++、java、Python等）均能使用

# 缺点

1、只是一个rpc框架，并不提供服务发现、依赖治理等soa中必要功能
