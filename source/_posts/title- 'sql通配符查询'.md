---
title: 'sql通配符查询'
---
---
<!--more-->
#### 在搜索数据库时，可以使用sql通配符，通配符通常代表**一个**或者**多个**字符，通配符必须和`like`一起使用。
| 通配符 | 描述 |
|  ---| :---|
|%|表示一个或者多个字符|
|_|表示一个字符|
|[charlist]|字符列表中的任何单一字符|
|[^charlist]或者[!charlist]|不在字符列表中的任意单一字符|
###例子：
```
//城市以Ne开头的数据
SELECT * FROM Persons WHERE City LIKE 'Ne%'；
//城市包含lond的数据
SELECT * FROM Persons WHERE City LIKE '%lond%'
//名字的第一个字符之后是eorge的人
SELECT * FROM Persons WHERE FirstName LIKE '_eorge'
//_表示一个字符
SELECT * FROM Persons WHERE LastName LIKE 'C_r_er'
//城市名称的首字母以A、L、N 开头的数据
SELECT * FROM Persons WHERE City LIKE '[ALN]%'
//城市首字母不以A、L、N 开头的数据
SELECT * FROM Persons WHERE City LIKE '[!ALN]%'
```
**注意:**
查询内容包含通配符时：


　　由于通配符的缘故，导致查询特殊字符“%”、“_”、“[”的语句无法正常实现，把特殊字符用“[]”括起来便可以正常查询。
例子：
```
　　function sqlencode(str)
　　str=replace(str,"[","[[]") '此句一定要在最前
　　str=replace(str,"_","[_]")
　　str=replace(str,"%","[%]")
　　sqlencode=str
　　end function
```

