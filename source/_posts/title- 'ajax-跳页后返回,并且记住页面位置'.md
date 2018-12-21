---
title: 'ajax-跳页后返回,并且记住页面位置'
---
---
<!--more-->
> 记住产品列表页的html并存贮.返回的时候直接赋值
```
                var htm = $(".classify_more_main").html();
                var page = $("#page").val();
                var category = $("#categoryId").val();
                var position = $(window).scrollTop();
                localStorage.setItem("htm", htm);
                localStorage.setItem("page", page);
                localStorage.setItem("category", category);
                localStorage.setItem("position", position);
```
把当前页面的位置信息和分类信息存储到`localStorage`,返回的时候在取出来一一赋值
```
                    var htm = localStorage.getItem("htm");
                    var page = localStorage.getItem("page");
                    var position = localStorage.getItem("position");

                    $("#page").val(page);
                    $(".classify_more_main").append(htm);
                    $(window).scrollTop(position);
```



