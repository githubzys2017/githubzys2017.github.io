---
title: 'JS中关于数字精确到小数点后两位'
---
---
<!--more-->
>* 会四色五入
```
var num =2.446242342;
num = num.toFixed(2); // 输出结果为 2.45
```
>* 正则表达式
```Number(15.7784514000.toString().match(/^\d+(?:\.\d{0,2})?/))```
>* 最笨
```
function get()
{
    var s = 22.127456 + "";
    var str = s.substring(0,s.indexOf(".") + 3);
    alert(str);
}
```
>* 正则
```
onload = function(){
    var a = "23.456322";
    var aNew;
    var re = /([0-9]+.[0-9]{2})[0-9]*/;
    aNew = a.replace(re,"$1");
    alert(aNew);
}
```
>* 原始
```
var num=22.127456;
alert( Math.round(num*100)/100);
```
>* 其他
```
1.丢弃小数部分,保留整数部分
parseInt(5/2)
2.向上取整,有小数就整数部分加1
Math.ceil(5/2)
3,四舍五入.
Math.round(5/2)
4,向下取整
Math.floor(5/2)
```




