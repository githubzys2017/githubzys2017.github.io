---
title: 'java 判断浏览器问题'
---
---
<!---more--->
### **判断是否通过微信浏览器访问**
> 通过微信浏览器访问的标识`MicroMessenger`

![微信浏览器标识](http://oq8arr6l2.bkt.clouddn.com/TIM%E5%9B%BE%E7%89%8720171117105735.png)

#### java 判断
```
String ua = ((HttpServletRequest) request).getHeader("user-agent")
          .toLowerCase();
      if (ua.indexOf("micromessenger") > 0) {// 是微信浏览器
       
      }else{

      }
```





