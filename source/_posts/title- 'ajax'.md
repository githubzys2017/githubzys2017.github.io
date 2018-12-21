---
title: 'ajax'
---
---
<!--more-->
## XMLHttpRequest是AJAX的基础。
*******************
### 创建XMLRequest对象
```variable = new XMLHttpRequest```
**注意**：为了应对所有浏览器
```
var xmlhttp;
if (window.XMLHttpRequest)
  {// code for IE7+, Firefox, Chrome, Opera, Safari
  xmlhttp=new XMLHttpRequest();
  }
else
  {// code for IE6, IE5
  xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
  }
```
### XMLHttpRequest对象用于和服务器交换数据
#### 向浏览器发送请求：
```
xmlhttp.open("GET", "test1.txt", true);
xmlhttp.send();
```
open(method, url aysnc);
> * method:请求方法，GET和POST.
> * url:文件在服务器上的位置
> * aysnc:是否同步
send(String)
> * String :仅用于POST 请求

**下列情况请使用POST**
> * 无法使用缓存文件（更新服务器上的文件或数据库）
* 向服务器发送大量数据（POST 没有数据量限制）
* 发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠（解决乱码问题）

为了避免缓存，可以向请求地址加入动态数据
```
xmlhttp.open("GET", "1.txt?t="+Math.random(), true);
```

服务器的响应，请使用 XMLHttpRequest 对象的 responseText 或 responseXML 属性
responseText:获得字符串形式的响应数据。
responseXML:获得 XML 形式的响应数据。
************************
![截图](http://oq8arr6l2.bkt.clouddn.com/%E6%90%9C%E7%8B%97%E6%88%AA%E5%9B%BE20170526210814.png)






