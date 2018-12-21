---
title: 'JQuery选择器'
---
---
<!--more-->
# 元素选择器
```
$("p");              //选取<p>元素
$("p.intro");        //选取所有 class="intro" 的 <p> 元素。
$("p#demo");         //选取所有 id="demo" 的 <p> 元素
```
# 属性选择器
```
$("[href]");             //选取所有带有 href 属性的元素。
$("[href='#']");         //选取所有带有 href 值等于 "#" 的元素。
$("[href!='#']");        //选取所有带有 href 值不等于 "#" 的元素。
$("[href$='.jpg']");     //选取所有 href 值以 ".jpg" 结尾的元素。
```
# CSS选择器
```
$("p").css("background-color","red");   //素有<p>元素的背景颜色改为红色
```
# 其他选择器
```
$(this);                //当前HTML元素
$("ul li:first");       //每一个<ul>元素中的第一个<li>元素
$("div#intro .head")；  //id="intro"的<div>元素中所有class="head"的元素
$(".intro.demo")；      //class="intro"且class="demo"的元素
$("p:first");           //第一个<p>元素
$("p:last");           //最后一个<p>元素
$("tr:even")；          //所有偶数的<tr>元素
$("tr:odd")；          //所有奇数的<tr>元素
$("ul li:eq(3)")；     //列表中的第四个元素（index 从 0 开始）
$("ul li:gt(3)")；     //列表中大于3元素
$("ul li:lt(3)")；     //列表中小于3元素
$(":contains('W3School')")；     //包含指定字符串的所有元素
$("p:hidden")；         //所有隐藏的<p>元素
```




