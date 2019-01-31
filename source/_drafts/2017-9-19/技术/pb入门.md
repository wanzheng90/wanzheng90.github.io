---
title: pb入门
date: 2017-02-18 16:36:10
tags:
---
PB(Protocol Buffers) 是一种轻便高效的结构化数据存储格式，可以用于结构化数据串行化，或者说序列化。它很适合做数据存储或 RPC 数据交换格式。可用于通讯协议、数据存储等领域的语言无关、平台无关、可扩展的序列化结构数据格式 。pb将数据转换为二进制。

<!--more-->

#  pb与json序列化后文件大小对比
对象如下：
![文件大小](/pic/size_example.png)
![文件大小](/pic/size_result.png)
pb序列化后文件大小约为json1/4

# pb序列化性能
pb序列化性能远高于json
![性能](/pic/perfermance_result.png)

# 使用示例
安装 protobuf 工具
```
git clone https://github.com/google/protobuf.git
cd protobuf
./autogen.sh
./configure
make
make check
sudo make install
```
编写proto文件
![proto](/pic/proto.png)
生成java代码
![protoc](/pic/protoc.png)

# Protobuf序列化原理
pb 采用整数变长编码，其规则如下：
  每个字节使用使用低7位表示数字，除了最后一个字节，其他字节的最高位都设置为1，例如：
数字1:
0000 0001
数字300：
1010 1100 0000 0010
  000 0010   010 1100
→  000 0010 ++ 010 1100
→  100101100
→  256 + 32 + 8 + 4 = 300
字段头
一个Protocol Buffers的消息包含一系列字段，每个字段由一个变长32位整数作为字段头，后面跟随字段体
字段头格式
```
(field_number << 3) | wire_type
-field_number:  字段序号
-wire_type:  字段编码类型
```
![格式](/pic/head_type.png)

编码示例1: 整数编码
```
message Test1 {
  required int32 a = 1;
}
```
a = 150时，编码如下
```
08 96 01
08:  1 << 3 | 0
96 01:
1010 1100 0000 0010
→ 010 1100 000 0010
→ 150
```

编码示例2: 字符串编码
```
message Test2 {
   required string b = 2;
}
```
b = "testing"时，编码如下
```
12 07 74 65 73 74 69 6e 67
12:  2 << 3 | 2
07:  字符串长度
74 65 73 74 69 6e 67
→ "testing"
```
