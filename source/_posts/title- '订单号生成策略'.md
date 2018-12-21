---
title: '订单号生成策略'
---
---
<!--more-->
### **订单号生成策略**

#### 唯一性
#### 安全性
#### 不能使用大规模随机码
#### 防止并发
#### 控制位数

### **怎么保证订单的唯一性**
#### 订单号命名规则来生成

> 比如“业务编码 + 时间戳 + 机器编号[前4位] + 随机4位数 + 毫秒数”。

#### 全局订单号数据生成池,生成订单
```
CREATE TABLE `order_id_generator` (
  `RANDOM_VALUE` bigint(20) NOT NULL,
  `ORDER_ID` int(11) NOT NULL,
  PRIMARY KEY (`RANDOM_VALUE`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

DROP PROCEDURE IF EXISTS `GET_ORDER_ID_FOR_REGISTER`;
DELIMITER ;;
CREATE DEFINER=`root`@`%` PROCEDURE `GET_ORDER_ID_FOR_REGISTER`()
BEGIN
    declare userMid int defau]\
```



