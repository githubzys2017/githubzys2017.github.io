---
title: 'JS获取地址栏参数'
---
---
<!--more-->
### 采用正则表达式获取地址栏参数
```

function GetQueryString(name)
{
     var reg = new RegExp("(^|&)"+ name +"=([^&]*)(&|$)");
     var r = window.location.search.substr(1).match(reg);
     if(r!=null)return  unescape(r[2]); return null;
}
 
// 调用方法
alert(GetQueryString("参数名1"));
alert(GetQueryString("参数名2"));
alert(GetQueryString("参数名3"));
```
URL(Uniform Resource Locator,URL)
完整的URL包括几部分：
scheme://host:port/path?query#fragment 
|    符号  |    意义  |
| :---   |:---|
|scheme|通信协议|
|host|主机（服务器、域名系统、主机名或IP地址）|
|post|端口号（可选参数，省略时为默认端口）|
|path|路径|
|query|参数|
|fragment|信息片段(锚点)|

### 练习
```
URL:http://www.maidq.com/index.html?ver=1.0&id=6#imhere
//获取整个URL字符串
window.location.href
//URL的协议部分
window.location.protocal
//主机部分（域名）
window.location.host
//端口部分
window.location.port
//路径部分
window.location.pathname
//参数部分
window.location.search
//锚点
window.location.hash
```

