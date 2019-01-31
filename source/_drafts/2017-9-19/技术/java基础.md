---
title: java基础
date: 2017-04-20 07:03:43
tags: java
category: java
---

### 语法基础


### 基础类库
Object
hashCode 目的？
hashCode返回一个int值。 在一个java执行期间，同一个对象返回的hashCode必须一致。但是程序的两个不同的运行期间，对象不必返回一样的hashCode
提供个hash值给HashTable使用，
1、如果两个对象equals为true，则hashCode必须一致
2、如果两个对象equals为false，hashCode可能一致
hashCode 一般就是内部地址，但是这个不是java语言规定的

equal 目的？
对比两个对象是否一致，默认是比较地址

HashMap
hashMap 不保证顺序，随时间变更顺序不变
hashmap 常用操作（put和get）提供了一个常数时间（算法的执行时间是一个常数，与数据大小和先前操作无关）性能。
0.75
大量的hashcode 一样的key会导致性能降低
 Map m = Collections.synchronizedMap(new HashMap(...))
 LinkedMap 与hashmap的区别，应用场景有何不同


### 多线程 
