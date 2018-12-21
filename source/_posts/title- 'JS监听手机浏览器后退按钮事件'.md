title: 'JS监听手机浏览器后退按钮事件'
---
---
<!--more-->

>转载地址：http://www.jb51.net/article/89921.htm


* 首先我们要了解浏览器的history。

>大家知道在页面中我们可以使用javascript window history，后退到前面页面，但是由于安全原因javascript不允许修改history里已有的url链接，但可以使用pushState方法往history里增加url链接，并且提供popstate事件监测从history栈里弹出url。既然有提供popstate事件监测，那么我们就可以进行监听。

### 返回、后退、上一页按钮点击监听实现代码：
```
window.addEventListener("popstate", function(e) {
    alert("我监听到了浏览器的返回按钮事件啦");//根据自己的需求实现自己的功能
}, false);
```
>虽然我们监听到了后退事件，但是页面还是会返回上一个页面，所以我们需要使用pushState增加一个本页的url,代表本页，大家都非常清楚是#

```
function pushHistory() {
    var state = {
    title: "title",
    url: "#"
    };
    window.history.pushState(state, "title", "#");
}
```

>当进入该页面，我们就给这个history压入一个本地的连接。当点击返回、后退及上一页的操作时，就进行监听，在监听代码中实现自己操作。

> 下面是完整的代码：

```
pushHistory();
window.addEventListener("popstate", function(e) {
    alert("我监听到了浏览器的返回按钮事件啦");//根据自己的需求实现自己的功能
}, false);
function pushHistory() {
    var state = {
    title: "title",
    url: "#"
    };
    window.history.pushState(state, "title", "#");
}
```

> PC端监听后退事件

```
$(document).ready(function(e) {

var counter = 0;
if (window.history && window.history.pushState) {
$(window).on('popstate', function () {
window.history.pushState('forward', null, '#');
window.history.forward(1);
window.location.href='/PF_ECP/po/kefumishu.shtml';//跳转到个人中心
});
}
window.history.pushState('forward', null, '#'); //在IE中必须得有这两行
window.history.forward(1);
});
```




