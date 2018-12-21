---
title: 'JS中获取当前时间戳问题'
---
---
<!--more-->
```
//第一种方法
var timeStamp = Date.parse(new Date());
//结果为1280977330000

//第二种方法
var timeStamp = (new Date()).valueof();
结果：1280977330748

//第三种方法
var timeStamp = new Date().getTime();
结果：1280977330748
```
> 第一种：获取的时间戳是把毫秒改成000显示

> 第二种和第三种是获取了当前毫秒的时间戳




