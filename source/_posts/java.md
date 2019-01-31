---
title: java
date: 2018-06-14 22:59:47
tags: java,基础类
---
总结java基础语句、语法及类库
<!-- more -->
# todo:
+ [ ]xorshift是怎样的

# Object

Object是所有对象的父类
包含的方法如下：

+ hashcode,返回对象的hash码  
  同一个对象的hashcode多次调用必须返回一致，否则在hashmap可能出现找不到的情况。
  与equal方法关联，两个对象hashcode相等，equal不需要相等，equal相等，hashcode必须相等。
  返回值可以通过java启动参数配置 -XX:hashCode=4，选择如下，默认5。默认并非地址的计算
  ```
  0、随机值
  1、内存地址 计算值
  2、硬编码1
  3、序列
  4、内存地址
  5、线程状态结合xorshift算法
  ```
> xorshift一种随机算法

+ equal,比较两个对象内容  
  与==异同，equal方法比较对象内存引用是否相等，equal比较两个对象内容是否一样。equal对象默认使用==比较  
  equals方法遵循如下规则：
  - 自反，x.equals(x)必为真
  - 对称，如果x.equals(y)为真,必然y.equals(x)为真
  - 传递，如果x.equals(y)为真,y.equal(z)为真,必然x.equals(z)为真
  - 一致，如果x.equals(y)为真，如果x、y没有修改，则x.equals(y)永为真
  - x.equals(null)永远为假

+ wait,让当前线程进入等待，直到被notify、notifyAll方法唤醒。 线程会释放当前对象monitor
    为何等待方法在object对象上而不在thread对象上，是因为java的monitor是在对象上。**注意：只有当前线程获取到对象monitor时才能调用此方法（即必须在synchronize中才能使用)，否则会抛出java.lang.IllegalMonitorStateException异常**

+ notify 唤醒第一个等待该对象锁的线程，让其等待获取monitor。  
  线程调用notify()之后，只有该线程完全从 synchronized代码里面执行完毕后，monitor才会被释放，被唤醒线程才可以真正得到执行权。
  **注意：只有当前线程获取到对象monitor时才能调用此方法（即必须在synchronize中才能使用)，否则会抛出java.lang.IllegalMonitorStateException异常**

+ notifyAll 唤醒所有在对象锁上等待的线程，让其竞争monitor，被唤醒线程会一直等待获取monitor
  **注意：只有当前线程获取到对象monitor时才能调用此方法（即必须在synchronize中才能使用)，否则会抛出java.lang.IllegalMonitorStateException异常**

+ getClass,获取对象元类型

+ toString,打印对象信息

+ finalize，垃圾回收是调用。最多只会调用一次

# String

# System

+ gc,gc方法调用垃圾回收  
  垃圾回收是另外一个线程控制



# collection

# map
