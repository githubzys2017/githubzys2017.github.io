---
title: 'JQuery——ajax()'
---
---
<!--more-->
#JQuery选择器

```
$(".new_product .caption a").click(function () {
            var productId = $(this).attr("productId")
            alert(productId)
            $("#order_box").show();

        })
```
**解析**：
>+ 找到class=“new_product”的元素，的子元素中class=“caption”的子元素中的`<a>`标签,绑定点击事件，点击时触发。
+ 通过`<a>`标签，得到其中的`productId`属性值。
+ 提醒`productId`的值。
+ 找到`id="order_box"`的元素，并显示
#ajax
###load()方法
```$(selector).load(URL,data,callback);```
> * url:必选参数。
* data:与请求一同发送的查询字符串键/值对集合.
* callback:load()方法完成后所执行的函数

示例代码：
```
$("#div1").load("demo_test.txt");       //把请求文件放入指定div中
$("#div1").load("demo_test.txt #p1");   //把指定文件中id=p1的内容放入div中
```
callback的示例代码：
```
$("button").click(function(){
  $("#div1").load("demo_test.txt",function(responseTxt,statusTxt,xhr){
    if(statusTxt=="success")
      alert("外部内容加载成功！");
    if(statusTxt=="error")
      alert("Error: "+xhr.status+": "+xhr.statusText);
  });
});
```
> * GET 基本上用于从服务器获得（取回）数据。注释：GET 方法可能返回缓存数据。
* POST 也可用于从服务器获取数据。不过，POST 方法不会缓存数据，并且常用于连同请求一起发送数据。

JQuery $.get()方法
```$.get(url, callback);```

jQuery $.post() 方法
```$.post(url, data, callback);```

# JQuery ajax()
示例代码：
```
$(document).ready(function(){
  $("#b01").click(function(){
  htmlobj=$.ajax({url:"/jquery/test1.txt",async:false});
  $("#myDiv").html(htmlobj.responseText);
  });
});
```
## ajax()的参数
> * data:（String）请求参数,**必须为 Key/Value 格式**
> * dataType:(String) 返回数据类型，
>    * xml": 返回 XML 文档，可用 jQuery 处理。
>    * "html": 返回纯文本 HTML 信息；包含的 script 标签会在插入 dom 时执行。
>    * "script": 返回纯文本 JavaScript 代码。不会自动缓存结果。除非设置了 "cache" 参数。注意：在远程请求时(不在同一个域下)，所有 POST 请求都将转为 GET 请求。（因为将使用 DOM 的 script标签来加载）
>     * "json": 返回 JSON 数据 。
>     * "jsonp": JSONP 格式。使用 JSONP 形式调用函数时，如 "myurl?callback=?" jQuery 将自动替换 ? 为正确的函数名，以执行回调函数。
>    *"text": 返回纯文本字符串
> * error:请求失败时调用次函数
> * success:请求成功后的回调函数
> * timeout:设置请求超时的时间（单位：毫秒）
> * type:GET,POST,(PUT,DELETE,仅部分浏览器支持)
> * url:请求地址

```
jquery   ajax
	参数为键值对形式 var data = {};
	为JSON变量 data赋值	data["id"] = 123456;
						data["value"] = 2345678;
	ajax 格式 	$.ajax({
						url:
						data:
						type:
						dataType:
						success: function(e){
							注意：e为返回的数据
							回调函数（自己的逻辑）
						}
						error: function(e){
							回调函数（自己的逻辑）
						}
						
						});
```




