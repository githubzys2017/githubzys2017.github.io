---
title: 'sql学习'
---
---
<!--more-->
## 注意：sql 对大小写不敏感。
## SQL包括两部分：
* 数据操作语言（DML）
* 数据定义语言（DDL）

### 数据操作语言（DML）：
* select --在数据表中查询。
* delete --在数据表中删除。
* update --更新数据表中的数据。
* insert into --在数据表中插入数据。
### 数据定义语言（DDL）:
* create database --创建数据库。
* alter database --修改数据库。
* create table --创建新表。
* alter table --修改数据库表。
* drop table --删除表。
* create index --创建索引。
* drop index --删除索引。
#### SELECT 语法：
> SELECT 列名称 FROM 表名称
> SELECT DISTINCT 列名称 FROM 表名称
    * 去除列上的重复信息
#### SQL WHERE 语法：
> SELECT 列名称 FROM 表名称 WHERE 列 运算符 值
###### where 语句中使用的运算符
在sql查询中 文本值必须被`''`单引号围绕，数字不能加单引号。
|   运算符   |   描述     |
| :----  |   :----|
|=| 等于    |
|<>  |    不等于     |
|&gt;=  |    大于等于    |
|<=   |    小于等于   |
|BETWEEN|  在某个范围内 |
|LIKE| 某种搜索模式   |
> SQL AND & OR 运算符
如果第一个条件和第二个条件都成立，则 AND 运算符显示一条记录。
如果第一个条件和第二个条件中只要有一个成立，则 OR 运算符显示一条记录。
#### ORDER BY 子句
> 根据指定的列对结果集进行排序，默认为升序；
> ASC 升序
> DESC 降序
### INSERT INTO 语句
> INSERT INTO 表名称 VALUES (值1, 值2,....)
> INSERT INTO table_name (列1, 列2,...) VALUES (值1, 值2,....)
### UPDATE 语句
> UPDATE 表名称 SET 列名称1 = 新值， 列名称2 = 新值 WHERE 列名称 = 某值
### DELETE 语句
> DELETE FROM 表名称 WHERE 列名称 = 某值
##### 在不删除表的情况下删除所有数据
> DELETE FROM 表名称
### LIMIT 子句
> LIMIT 子句用于规定要返回的记录的数目。
> SELECT 列名称 FROM 表名称 LIMIT 数据数量；
### LIKE 操作符
> LIKE
> NOT LIKE
##### SQL 通配符
|    符号   |      描述      |
|   :----   |    :-----   |
| %  |  代替一个或多个字符|
| _   |   仅代替一个字符   |
|[charlist]| 字符列中的任何单一字符|
|[^charlist]或者[!charlist]|不在字符列中的任何单一字符|
##### 例子：
```
SELECT * FROM Persons WHERE City LIKE 'Ne%'
SELECT * FROM Persons WHERE City LIKE '%lond%'
SELECT * FROM Persons WHERE FirstName LIKE '_eorge'
SELECT * FROM Persons WHERE City LIKE '[ALN]%'
SELECT * FROM Persons WHERE City LIKE '[!ALN]%'
```
####IN 操作符
> SELECT 列名称 FROM 表名称 WHERE 列名称 IN (值1,值2,...)

#### BETWEEN 操作符
```
SELECT 列名称 FROM 表名称 WHERE 列名称 BETWEEN value1 AND value2
```
#### SQL Alias（别名）
```
//表别名
SELETE 列名称 FROM 表名称 AS 别名;
//列别名
SELETE 列名称  AS 别名 FROM 表名称;
```
#### SQL JOIN
SQL join 用于根据两个或多个表中的列之间的关系，从这些表中查询数据。
```
SELECT 列名称 FROM 表名称 a INNER JOIN 表名称 b ON a.主键 = b.主键 ORDER BY 列名称。
```
JOIN 的各种类型：

* JOIN: 如果表中有至少一个匹配，则返回行。
* LEFT JOIN: 即使右表中没有匹配，也从左表返回所有的行
* RIGHT JOIN: 即使左表中没有匹配，也从右表返回所有的行
* FULL JOIN: 只要其中一个表中存在匹配，就返回行

### SQL UNION 和 UNION ALL 操作符
* UNION 操作符用于合并两个或多个 SELECT 语句的结果集。
    注意：UNION 操作符选取不同的值
### SQL SELECT INTO 语句
### SQL CREATE DATABASE 语句
* 创建数据库
* CREATE DATABASE 数据库名称；

### SQL CAEATE TABLE
* 在数据库中创建表

``` 
CREATE TABLE 表名称
(
列名称1 数据类型,
列名称2 数据类型,
列名称3 数据类型,
....
)
```
表结构中的数据类型

|  数据类型   |     描述    |
|  :---    |     :----  |
| integer(size)，int(size), smallint(size)， tinyint(size)| 仅容纳整数，括号内规定数字的最大位数|
|decimal(size, d), numeric(size, d)|容纳带有小数的数字。“size”规定数字的最大位数，“d”规定小数点右侧的最大位数|
|char(size)| 容纳固定长度的字符串，括号内为字符串的长度|
|varchar(size)| 容纳可变长度的字符串，括号内为字符串的最大长度。|
|data(yyyymmdd)|容纳日期|
### SQL 约束 (Constraints)
约束用于限制加入表的数据类型。
**注意：** 可以在创建表时规定约束，或者在表创建之后添加约束。
几种约束类型：

* NOT NULL  ---非空约束，
* UNIQUE   - [ ] 置顶的第一个任务是专注任务 ---字段数据唯一约束，可以多个字段添加
* PRIMARY KEY   --主键约束，值唯一，并且不能为空
* FOREIGN KEY   --外键约束
* CHECK KEY
* CHECK --用于限制列中的值得范围
* DEFAULT   --默认约束，用于向表中添加默认值
### SQL CREATE INDEX 创建索引
*备注* 在不读取整个表的情况下，更快的查询数据库。
#### SQL CREATE INDEX 语法
```
在表上创建一个简单的索引。允许使用重复的值：
CREATE INDEX index_name ON table_name (column_name)
```
#### SQL CREATE UNIQUE INDEX 语法
```
在表上创建一个唯一的索引
CREATE UNIQUE INDEX index_name ON table_name (column_name)
```
### SQL 撤销索引、表以及数据库
```
//删除索引
ALTER TABLE table_name DROP INDEX index_name
//删除表
DROP TABLE 表名称
//删除数据库
DROP DATABASE 数据库名称
//只删除表中的数据
TRUNCATE TABLE 表名称
```
### SQL ALTER TABLE 语句
用于在已存在的表中添加、修改、删除列。
```
//在表中添加字段
ALTER TABLE table_name ADD column_name datatype
//在表中删除字段
1. ALTER TABLE table_name DROP COLUMN column_name
//改变表中字段的数据类型
2. ALTER TABLE table_name AlTER COLUMN column_name datatype
```
### SQL AUTO INCREMENT 字段
自动增加字段，MySQL AUTO_INCREMENT.其默认开始值为1，并且每条记录递增1。
```
//设定起始值为100
ALTER TABLE Persons AUTO_INCREMENT=100
```
### SQL Date 函数
MySQL 內建日期函数
|    函数   |    描述     |
|   :----   |   :----  |
|NOW()  |返回当前的日期和时间|
|CURDATE()| 返回当前的日期|
|CURTIME()|返回当前时间|
|DATA()|提取日期或日期/时间表达式的日期部分|
|EXTRACT()|返回日期/时间的单独部分|
|DATE_ADD()|给日期添加指定的时间间隔|
|DATE_SUB()|从日期减去指定的时间间隔|
|DATEDIFF()|返回两个日期之间的天数|
|DATE_FORMAT|用不同的格式显示日期/时间|
### IFNULL 函数
```
//如果字段为null,则返回0
SELECT 字段名,字段名*(字段名+IFNULL(字段名1,0)) FROM 表名称
```

## SQL 函数
* AVG() 求平均数。
* COUNT()   统计（行）函数。
```
//返回列中不重复的数据个数
SELECT COUNT(DISTINCT Customer) AS NumberOfCustomers FROM Orders
```
* FIRST() 函数  返回指定字段中第一个记录
* LAST()    返回指定字段的最后一个记录
* MAX()     返回一列中的最大值（不包括NULL）
* MIN()     返回一列中的最小值（不包括NULL）
* SUM()     返回数值列的总数（总额）
* GROUP BY 语句     根据指定字段对结果进行分组
* HAVING 子句   WHERE关键字无法和合计函数一起使用
* UCASE() 函数      把字段的值转换为大写
* LCASE() 函数      把字段的值转换为小写
* MID() 函数        从文本字段中提取字符
```
//语法
SELECT MID(column_name,start[,length]) FROM table_name
```
* LEN() 函数  返回文本字段中值得长度
* ROUND() 函数      把数值字段舍入为指定的小数位数
* FORMAT() 函数     对字段的显示进行格式化
```
SELECT FORMAT(column_name,format) FROM table_name
```






