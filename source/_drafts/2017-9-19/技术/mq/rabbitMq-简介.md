---
title: rabbitMq-简介
date: 2017-07-31 23:18:58
category: rabbitMq
tags: rabbitMq,技术
---
# 1.应用模型
生产消费者
发布订阅
rpc

# 2.实现模型
exchange：核心概念，负责将消息路由到对应队列中。类比于邮局，将信件（message）转发到对应邮箱（queue）
queue：核心概念，消息队列，负责将消息发送给消息接受方。类似于邮箱
binding：绑定exchange与queue，并确定exchange于queue之间的消息路由关系
vhost：虚拟空间，将用户、exchange、queue隔离为单独空间进行管理
worker：应用实例
channel：queue与consumer消息通道，queue的消息分发及负载均衡是基于channel的而非应用，也就是说如果一个应用与queue建立的多个channel，会被当做不同的消费者。一个应用可以与broker建立多个channel，但是这些channel可以共享同一个tcp连接。

# 3.AMQP协议
![传输层层级](./pic/传输层层级.png)
![传输层层级任务分类](./pic/传输层层级任务分类.png)

