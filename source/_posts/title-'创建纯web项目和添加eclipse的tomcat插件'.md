---
title:'创建纯web项目和添加eclipse的tomcat插件'
---
---
<!--more-->
### 创建纯web项目
#### 对于java中web项目和传统的java项目只是项目结构的区别,例如:
![项目结构](http://oq8arr6l2.bkt.clouddn.com/TIM%E5%9B%BE%E7%89%8720180308215357.png)
#### 并且需要修改字节码文件存储位置,因为传统项目是放在**/bin**目录下,而web项目需要放在**/WEB-INF/classes**下:
![修改字节码文件存储路径](http://oq8arr6l2.bkt.clouddn.com/TIM%E5%9B%BE%E7%89%8720180308215557.png)

### eclipse添加tomcat插件
#### eclipse安装插件有多种方法,本文只介绍一种:
> 插件引用文件的存放地址,eclipse下
![文件路径](http://oq8arr6l2.bkt.clouddn.com/TIM%E5%9B%BE%E7%89%8720180308220710.png)
>插件存放地址,自定义,文件里的内容:
![文件内容](http://oq8arr6l2.bkt.clouddn.com/TIM%E5%9B%BE%E7%89%8720180308220747.png)
> 制作插件的格式:
![格式](http://oq8arr6l2.bkt.clouddn.com/TIM%E5%9B%BE%E7%89%8720180308221344.png)

### 通过配置文件的方式部署web项目
![](http://oq8arr6l2.bkt.clouddn.com/TIM%E5%9B%BE%E7%89%8720180308221817.png)




