# DDL语句

## 一、数据库  
> - 查询所有数据库  
```mysql
SHOW DATABASES;
```

> - 查询当前数据库
```mysql
SELECT DATABASE();
```

> - 创建数据库
```mysql
CREATE DATABASE IF [NOT EXISTS] 数据库名 [DEFAULT CHARSET 字符集（如UTF-8等）] [COLLATE 排序规则];
```

> - 删除数据库
```mysql
DROP DATABASE [IF EXISTS] 数据库名;
```

> - 使用数据库（切换到某一个数据库）
```mysql
USE 数据库名;
```

## 二、表操作-查询
> - 查询当前数据库所有表  
```mysql
SHOW TABLES;
```  

> - 查询表结构  
```mysql
DESC 表名;
```

> - 查询指定表的建表语言  
```mysql
SHOW CREATE TABLE 表名;
```

## 三、数据类型    
### 1、数值类型  
> - **① 整数型**

|类型 |占内存 |数值范围 |
| ---- | ---- | ---- |
|TINYINT |1字节 |-128 ~ 127 / 0 ~ 255|
|SMALLINT | 2字节 |-32766 ~ 32765 / 0 ~ 65535|
|MEDIUMINT |3字节 |-8388608 ~ 8388607 / 0 ~ 16777215|
|INT/INTEGER |4字节 |-2147483648 ~ 2147483647 / 0 ~ 4294967295|
|BIGINT |8字节 |$-2^{63}$ ~ $2^{63}$ / 0 ~ $2^{64}$|

> - **② 浮点型**

|类型 |内存 |
| ---- | ---- |
|FLOAT |4字节 |
|DOUBLE |8字节 |
|DECIMAL |5 ~ 17字节 |  
> > - 注意：decimal(p, s)用于存储固定精度和比例的数字，p参数指示可以存储的最大位数（必须是1 ~ 38之间的值，默认18），s指示小数点右边存储的最大位数（必须是0 ~ p之间的值）  

> - **③字符串类型**

|类型 |叙述 |内存 |
|---|---|---|
|CHAR |定长字符串 |0 ~ 255字节 |
|VARCHAR |变长字符串 |0 ~ 65535字节 |
|TINYBLOG |不超过255个字符的二进制数据 |0 ~ 255字节 |
|BLOG |二进制形式长文本数据 |0 ~ 65535字节 |
|MEDIUMBLOG |二进制形式中等长度文本数据 |0 ~ 16777215字节 |
|LONGBOLG |二进制形式极大文本数据 |0 ~ 4294967295字节 |
|TINYTEXT |短文本字符串 |0 ~ 255字节 |
|TEXT |长文本字符串 |0 ~ 65535字节 |
|MEDIUMTEXT|中等长度文本数据 |0 ~ 16777215字节 |
|LONGTEXT |极大文本数据 |0 ~ 4294967295字节 |  

> > - 注意：使用char和varchar时，其后面必跟括号和数字，表示最大允许长度
> > > - char(10):必占10个空间 $\rightarrow$ 性能好   
> > > - varchar(10):不一定占10个空间 $\rightarrow$性能差些，因为要计算占多少长度  

> - **④日期数据类型**  

|类型 |占内存 |范围 |
|---|---|---|
|DATE|3字节|1000-01-01 ~ 9999-12-31|
|TIME|3字节|-839:59:59 ~ 838:59:59|
|YEAR|1字节|1901 ~ 2155|
|DATETIME|8字节|1000-01-01 00:00:00 ~ 9999-12-31 23:59:59|
|TIMESTAMP|4字节|1000-01-01 00:00:00 ~ 2038-01-19 03:14:07|

## 四、表操作-创建  

> - 创建  
```mysql
CREATE TABLE 表名(
   字段1 字段1类型 COMMENT 字段1注释  
   字段2 字段2类型 COMMENT 字段2注释
   ······
   字段n 字段n注释 COMMENT 字段n注释
) COMMENT 表注释;
```

## 五、表操作-修改

> - 添加字段  
```mysql
ALTER TABLE 表名 ADD字段名 类型 [COMMENT 注释] [约束];
```

> - 修改数据类型
```mysql
ALTER TABLE 表名 MODIFY 字段名 新类型;
```

> - 修改字段名和字段类型
```mysql
ALTER TABLE 表名 CHANGE 旧字段 新字段名 类型 [COMMENT 注释] [约束];
```

> - 删除字段  
```mysql
ALTER TABLE 表名 DROP 字段名;
```

> - 修改表名
```mysql
ALTER TABLE 表名 RENAME TO 新表名;
```
> - 删除表(两种方法)
```mysql
DROP TABLE [IF EXIST] 表名;
```
```mysql
TRUNCATE TABLE 表名;
```
> > - **注：二者区别在于第二种truncate是删除表并重新创建该表，共同点在于都会删除表中的数据**


## 六、例
```mysql
# 查询所有的数据库
show databases;

# 查询当前的数据库
select database();

# 创建一个数据库
create database if not exists mydata1 default charset utf-8mb4 collate utf8mb4_unicode_ci;

# 使用mydata1
use mydata1

# 创建表
create table emp(
    id int  comment '编号',
    workno varchar(10) comment '工号',
    name varchar(10) comment '姓名',
    gender char(1) comment '性别',
    age tinyint unsigned comment '年龄',
    idcard char(18) comment '身份证号',
) comment '员工表';

# 添加字段
alter table emp add workaddress varchar(50) cmmment '工作地址';
alter table emp add entrydate date cmmment '入职时间';
```


