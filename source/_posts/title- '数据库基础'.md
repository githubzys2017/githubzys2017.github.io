---
title: 'MySQL 数据库的基础'
---
tag:
---
<!--more-->
### MySQL 安装方式
> * MSI 安装包方式安装
> * ZIP 解压方式

#### MySQL 配置修改
##### 修改默认编码方式
> * 安装目录 --> my.ini
> * --> [client] --> port=3306
> * --> [mysql] --> default-character-set=utf8
> * --> [mysqld] 服务器端配置

#### 登录mysql 
##### 登录和退出
> * mysql -uroot -p -P3306 -h127.0.0.1
> * 服务名 用户名 密码 端口号 服务器地址
> * exit

#### 修改命令提示符
> * prompt 提示符

#### SQL语句规范
* 关键字和函数名称全部大写
* 数据库名称, 表名称 字段名称全部小写
* SQL语句必须以分号结尾

###### 查看版本号
* SELECT VERSION();

###### 设置编码格式
* SET NAMES XXX;

###### 修改默认结束符
* DELIMITER //
**将默认结束符";"修改为"//"**

###### 查看当前时间
* SELECT NOW();

###### 创建数据库
* CREATE {DATABASE | SCHEMA} [IF NOT EXISTS] db_name [DEFAULT] CHARACTER SET [=] charset_name

###### 打开数据库
* USE 数据库名称

###### 查看数据库的结构
* DESC tbl_name;

###### 当前用户打开的数据库
* SELECT DATABASE();

###### 修改数据库
* ALTER {DATABASE | SCHEMA} [db_name] [DEFAULT] CHARACTER SET [=] charset_name

###### 删除数据库
* DROP {DATABASE | SCHEMA} [IF EXISTS] db_name

#### 数据类型
###### 整型
|数据类型|字节|
|:--|--:--|
|TINYINT|1|
|SMALLINT|2|
|MEDIUMINT|3|
|INT|4|
|BIGINT|8|
###### 浮点型
|数据类型|存储范围|
|:--|--:--|
|FLOAT[(M, D)]|小数点后7位|
|DOUBLE[(M, D)]||
**备注** M是数字的总位数, D是小数点后的位数.

#### 操作表
###### 创建表
> CREATE TABLE [IF NO EXISTS] table_name(
&nbsp;&nbsp;&nbsp;&nbsp;      column_name data_type,
&nbsp;&nbsp;&nbsp;&nbsp;    ......
)

###### 修改表
* 添加单列 ALTER TABLE tbl_name ADD [COLUMN] col_name column_definition [FIRST |  AFTER col_name];
* 删除列 ALTER TABLE tbl_name DROP [COLUMN] col_name;

###### 添加约束
* 添加主键约束 ALTER TABLE tbl_name ADD [CONSTRAINT[symbol]] PRIMARY KEY [index_type] (inde_col_name,...)
* 添加唯一约束 ALTER TABLE tbl_name ADD [CONSTRAINT[symbol]] UNIQUE KEY [index_type] (inde_col_name,...)
* 添加外键约束 ALTER TABLE table_name ADD [CONSTRAINT [symbol]] FOREIGN KEY [index_name] (index_col_name, ...) reference_definition
###### 修改约束
* 添加/删除默认约束 ALTER TABLE table_name ALTER [COLUMN] col_name {SET DEFAULT literal | DROP DEFAULT}
* 删除主键约束 ALTER TABLE tbl_name DROP PRIMARY KEY
* 删除唯一约束 ALTER TABLE tbl_name DROP {INDEX|KEY} index_name
* 删除外键约束 ALTER TABLE tbl_name DROP FOREIGN KEY fk_symbol

###### 修改数据表
* 修改列定义 ALTER TABLE tbl_name MODIFY [COLUMN] col_name column_definition [FIRST|AFTER col_name]
* 修改列名称 ALTER TABLE tbl_name CHANGE col_name1  col_name2 column_definition [FIRST|AFTER col_name3]
* 数据表更名 ALTER TABLE tbl_name RENAME [TO|AS] new tbl_name
* 数据表更名 RENAME TABLE tbl_name TO new_tbl_name [, tbl_name,...]

###### 查看数据表列表
* SHOW TABLES [FROM db_name] [LIKE 'pattern' | WHERE expr]

###### 查看数据表的结构
* SHOW COLUMNS FROM tbl_name

###### 插入记录
* INSERT [INTO] tbl_name [(col_name,...)] VALUES(val,...)

###### 查找记录
SELECT expr,... FROM tbl_name

#### 约束
>|约束|名称|
|:--|:--|
|NOT NULL | 非空约束|
|PRIMARY KEY|主键约束|
|UNIQUE KEY| 唯一约束|
|DEFAULT|默认约束|
|FOREIGN KEY | 外键约束|

###### FOREIGN KEY 外键约束
> 1. 父表和子表必须使用相同的存储引擎, 禁止使用临时表
> 2. 存储引擎InnoDB.
> 3. 外键列和参照列必须具有相似的数据结构.数字的长度和是否有符号位必须相同;而字符的长度则可以不同.
> 4. 外键列和参照列必须创建索引

###### 外键约束的参照操作
> 1. CASCADE: 从父表删除或更新且自动删除或更新子表中匹配的行
2. SET NULL: 从父表删除或更新行,并设置子表的外键列为NULL.如果使用该选项.必须保证子表列没有指定NOT NULL.
3. RESTRICT: 拒绝对父表的删除或更新操作.
4 NO ACTION: 标准SQL的关键字, 在MSQL中与RESTRICT相同

###### 显示索引
* SHOW INDEXES FROM provinces;

###### 查询表结构
* SHOW COLUMNS FROM tbl_name;

###### 插入记录
* INSERT [INTO] tbl_name [(col_name,...)] {VALUES|VALUE} ({expr|DEFAULT},...),(...),...
* INSERT [INTO] tbl_name SET col_name={expr|DEFAULT},...
*与第一种的区别,此方法可以使用子查询*
* INSERT [INTO] tbl_name [(col_name,...)] SELECT ...
*此方法可以将查询结果插入到指定数据表.*

###### 更新记录
* 单表更新 UPDATE [LOW_PRIORITY] [IGNORE] table_reference SET col_name1={expr1|DEFAULT} [, col_name2={expr2|DEFAULT}]... [WHERE where_condition]
* 多表更新 UPDATE table_references SET col_name1 = {expr1|DEFAULT} [, col_name2 = {expr2|DEFAULT}]...[WHERE where_condition]

###### 删除记录
* 单表删除 DELETE FROM tbl_name [WHERE where_condition]
* 多表删除 DELETE tbl_name[.*] [, tbl_name[.*]]... FROM table_references [WHERE where_condition]

###### 清除mysql表中的数据
* DELETE FROM tbl_name;(不记录日志,删除后不能恢复)
**不带WHERE参数可以删除表中的所有内容**
* TRUNCATE TABLE  tbl_name;(保留数据结构,重新创建表)

###### 查找记录
* SELECT select_expr [, select_expr...]  
[  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[FROM table_references]  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[WHERE where_condition]   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[GROUP BY {col_name|position} [ASC | DESC],...]   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[HAVING where_condition]  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ORDER BY {col_name | expr | position} [ASC|DESC],...]   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[LIMIT {[offset,] row_count | row_count OFFSET offset}]
]


#### 子查询
> ANY
> SOME
> ALL

###### CREATE... SELECT
* 创建数据表同时将查询结果写入到数据表
* CREATE TABLE [IF NOT EXISTS] tbl_name [(create_definition,...)] select_statement

###### 连接查询
* INNER JOIN, 内连接 , *在mysql中, JOIN, CROSS JOIN 和 INNER JOIN是等价的*
**仅显示符合连接条件的记录**
* LEFT [OUTER] JOIN, 左外连接
**显示左表中的全部和右表中符合条件的记录**
* RIGHT [OUTER] JOIN, 右外连接
**显示右表中的全部和左表中符合条件的记录**

#### 运算符和函数
###### 字符函数
|函数名称|描述|
|:--|:--|
|CONCAT()|字符连接|
|CONCAT_WS()|使用指定的分隔符进行字符连接|
|FORMAT()|数字格式化|
|LOWER()|转换成小写字母|
|UPPER()|转换成大写字母|
|LEFT()|获取左侧字符|
|RIGHT()|获取右侧字符|
|LENGTH()|获取字符串长度|
|LTRIM()|删除前导空格|
|RTRIM()|删除后续空格|
|TRIM()|删除前导和后续空格|
|SUBSTRING()|字符串截取|
|[NOT] LIKE|模式匹配|
|REPLACE()|字符串替换
###### 数值运算符和函数
|名称|描述|
|:--|:--|
|CEIL()|进一取整|
|DIV|整数触发|
|FLOOR|舍一取整|
|MOD|取余数(取模)|
|POWER()|幂运算|
|ROUND|s四舍五入|
|TRUNCATE()|数字截取|
###### 比较运算符与函数
|名称|描述|
|:--|:--|
|[NOT] BETWEEN...AND...|[不]在范围之内|
|[NOT] IN()|[不]在列出值范围内|
|IS [NOT] NULL|[不]为空|
###### 日期时间函数
|名称|描述|
|:--|:--|
|NOW()|当前日期和时间|
|CURDATE()|当前日期|
|CURTIME()|当前时间|
|DATA_ADD()|日期变化(**INTERVAL XX DAY**)(DAY, WEEK, YEAR)|
|DATEDIFF()|日期差值|
|DATE_FORMAT()|日期格式化|
###### 信息函数
|名称|描述|
|:--|:--|
|CONNECTION_ID()|连接ID|
|DATABASE()|当前数据库|
|LAST_INSERT_ID()|最后插入记录的id号|
|USER()|当前用户|
|VERSION()|版本信息|
###### 聚合函数
|名称|描述|
|:--|:--|
|AVG()|平均值|
|COUNT()|计数|
|MAX()|最大值|
|MIN()|最小值|
|SUM()|求和|
###### 加密函数
|名称|描述|
|:--|:--|
|MD5()|信息摘要算法|
|PASSWORD()|密码算法|
###### 自定义函数
* 删除自定义函数 DROP FUNCTION function_name
* 创建自定义函数 CREATE FUNCTION function_name RETURNS {STRING|INTEGER|REAL|DECIMAL} routine_body
> 1. 函数体由合法的SQL语句构成;
> 2. 函数体可以是简单的SELECT或INSERT;
> 3. 函数体如果为复合结构则使用BEGIN...END语句;
> 4. 复合结构可以包含声明, 循环, 控制结构;

#### 存储过程
> 存储过程是SQL语句和控制语句的预编译集合, 以一个名称存储并作为一个单元处理
##### 存储过程的优点
* 增强SQL语句的功能和灵活性
* 实现了较快的执行速度
* 减少了网络流量

###### 创建存储过程
* CREATE [DEFINER = {user|CURRENT_USER}] PROCEDURE sp_name ([proc_parameter[,...]]) [characteristic...] routine_body proc_parameter: [IN|OUT|INOUT] param_name type
* IN , 表示该参数的值必须在调用存储过程时指定
* OUT, 表示该参数的值可以被存储过程改变, 并且可以返回
* INOUT, 表示该参数的调用时指定, 并且可以被改变和返回

###### 过程体
* 过程体由合法的SQL语句构成
* 过程体可以是任意SQL语句
* 过程体如果为复合结构则使用BEGIN...END语句
* 复合语句可以包含声明,循环,控制语句;
* 参数列表的名字不能和数据库字段名相同

###### 调用存储过程
* CALL sp_name([parameter[,...]])
* CALL sp_name[()]

>  DELIMITER //
CREATE PROCEDURE removeUserById(IN id SMALLINT UNSIGNED)
BEGIN
DELETE FROM users WHERE id = id;
END
//
DELIMITER ;

###### 删除存储过程
* DROP PROCEDURE [IF EXISTS] sp_name

#### 声明变量
* 用户变量 SET @变量名 = value; | SELECT @变量名 := value
* 全局变量 SET GLOBAL var | SET @@global.var 所有客户端生效,只有super权限才可以设置全局变量
* 局部变量 declare c int default 0;
* 会话变量
> 设置会话变量有如下三种方式：
>> set session var_name = value;
>> set @@session.var_name = value;
>> set var_name = value;
> 查看一个会话变量也有如下三种方式：
>>select @@var_name;
>> select @@session.var_name;
> show session variables like "%var%";


#### 存储引擎
###### 分类
* MyISAM
* InnoDB
* Memory
* CSV
* Archive



