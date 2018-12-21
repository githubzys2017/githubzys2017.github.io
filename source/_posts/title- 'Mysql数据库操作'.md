---
title: 'Mysql数据库操作'
---
tags: [Mysql,数据库]
---
<!--more-->
### 更新数据库字段部分内容
#### 方法一：
```
update tab set A = concat(substring(A,1,3),'bbb');
-- 从A的1个字符开始取3个字符，加上'bbb'，再写入a中，如果A原始值为'123aaa'，那么更新之后为'123bbb'了。
update tab set A = concat(substring(字段, 开始位置（从1开始）,取几个字符),新值);
```
#### 方法二：
```
update table set a=REPLACE(a,'1','2'); 
-- 将字段A值中的包含的1，替换成2
update table set a=REPLACE(字段, 旧值, 新值);
```





