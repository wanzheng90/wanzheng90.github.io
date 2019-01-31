---
title: python基础语法学习
date: 2017-04-18 23:00:33
tags: python
category: python
---
# 注释
> 代码是写给人类读的，所以写注释很重要。注释是给人看的，机器不会执行
Python 代码以“#”头开始

```python
# 这是一行注释
```

# 值类型与变量定义
> 变量就是给内存取的一个名词。值类型告诉cpu该如何读取这块内存。变量赋值是告诉机器我想往这块内存中放啥值

```python
var1 = 100
```
var1就是变量名。类型为整形。=符号为赋值语句，表示将整数100写入var1变量所代表的内存中

python中常用的数据类型有：
Number(数值类型)，例如：1，2，0.1，10。整形表示数字
String(字符串),例如："1","5sdfd"
Array（数组），例如：[1,2,3],["23","sz"]
Tuple(元祖)，例如：（1,2,3）与数组不同在于元祖不能修改
Dictionary(字典)，例如：{'key':1,'key2':3}



# 逻辑控制
> 告诉机器如何做选择

Python if 语句
```
if 条件A成立 :
	执行代码A
elif 条件B成立 :
	执行代码B
else :
	都不成立执行此段代码
```
示例
```python
condition = 2
if condition ==1 :
	print('condition is 1')
elif condition == 2 :
	print('condition is 2')
else :
	print('condition is 3')
```

# 函数
> 就如写文章要有段落一样，没有良好段落的作文会得低分的

# 包
> 就像物品需要分文别类一样，这枚多庞大的代码也需要按照类别进行管理（类别也就叫做包）

# 库
> 就像买iPhone时，买到的是一台组装好的机器，而不是一堆零件。库也是别人封装好的代码，直接使用




