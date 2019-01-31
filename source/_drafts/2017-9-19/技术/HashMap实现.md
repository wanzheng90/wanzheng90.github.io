---
title: HashMap实现
date: 2017-04-24 13:59:43
tags: java
---
目的：
按照key-value的方式存储值
特性：
无论数据有多大，查找性能为常数级
源码特点:
hash时，会将key 对象的hash值高16位与低16位亦或处理，这是为了保持hash值的大体平均，能够使用到高位
Node[] table 保存hash table
node 分为 linked node、Tree node
treeNode 为红黑色，为一种改造类型的查找二叉树。查找二叉树是一种自平衡的二叉树，满足如下特性，它的左子树都比它的根节点小，它的右子树都比他的根节点大

