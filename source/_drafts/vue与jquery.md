---
title: vue与jquery
date: 2016-08-31 11:27:10
tags:
---

# 简单定义
+ jQuery 是一个前端js库。
+ vue是一个前端的vm库。

<!--- More --->

# jQuery与vue之间的关系

如果将浏览器比作数据库，dom比作数据库表，则jQuery、vue的位置如下：

| 浏览器  | 数据库     |
| :------------- | :------------- |
| dom操作API       | 每个数据库的驱动，如：mysql、SqlServer等  |
| jQuery  | jdbc |
| vue     | orm框架，如mybatis|

##### 说明：
dom操作API是js与dom交互最基本的方式，大部分接口根据规范是一致的，但有部分是特有实现接口。jQuery 屏蔽里各个浏览器之间dom操作之间的区别，同时简化了dom操作。vue 则通过数据驱动界面的方式，解耦js逻辑与dom操作。

# 示例
  一个简单的表单提交

## jQuery

````html````
<form>
  <input type="text" id="name">
  <button id="submit"></button>
</form>
<div id="msg"></div>
````

````javaScript````
  $('#submit').click(function(){
    var name = $('#name').val();
    $.$.ajax({
      url: '/names',
      type: 'post',
      dataType: 'html',
      data: {name: name}
    })
    .done(function(ret) {
      $('#msg').text(ret.msg);
    });
  });
````

## vue提交表单

````html````
<form id="form">
  <input type="text" id="name" v-model="name">
  <button id="submit" @click="submit"></button>
</form>
<div id="msg">{{msg}}</div>
````

````javaScript````
var formVue = new Vue({
  el:'#form',
  data:{
    name:''
  },
  methods:{
    submit:function(){
      addName(this.name);
    }
  }
});
var msgVue = new Vue({
  el:'#msg',
  data:{
    msg:''
  }
});
function addName(name) {
  $.ajax({
    url: '/names',
    type: 'post',
    dataType: 'json',
    data: {name: formVue.name}
  })
  .done(function(ret) {
    msgVue.msg = ret.msg;
  });
}
````

# 总结
  vue能做的事情，jQuery都能做，而且vue相对于jQuery并不能减少代码开发量。vue主要是通过数据驱动的方式将业务逻辑与dom操作进行分离。
