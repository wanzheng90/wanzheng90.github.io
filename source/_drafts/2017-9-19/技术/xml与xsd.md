---
title: xml与xsd
date: 2017-01-04 16:02:03
tags: xml
---
# xml 与xsd简介
xml 扩展标记语言，适合数据结构化表达
xsd xml验证文件，文件本身采用xml格式

<!-- more -->

## xml namespace

为了区分相同的元素名，可以用namespace 前缀来区分

```

<a:a xmlns:a="http://www.test.com"></a:a>

<b:a xmlns:b="http://www.test1.com"></b:a>  

<a xmlns="http://test2.com"></a>

```

xmlns属性定义namespace名称，如果没有设置namespace名称，则为默认

xsd 用来校验xml文件的xml文件，使用方法如下

```

<a xmlns="http://www.test.com/a" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  xsi:schemaLocation="http://www.test.com/a a.xsd"></a>

```

 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  shema默认配置，

xsi:schemaLocation="http://www.test.com/a a.xsd" shema namespace url对应的校验文件
