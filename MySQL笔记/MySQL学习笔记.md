# MySQL学习笔记

## 概述 

### 一、关于数据库
1、数据库相关
 - 数据库：存储数据的仓库（数据有组织的进行存储），最终存储数据的是表
 - 数据库管理系统：操纵、管理、维护数据库的大型软件，像是MySQL、Oracle等等
 - SQL（Structured Query Language）：操纵关系型数据库的编程语言，定义了一套操作关系型数据库的统一标准，不管在哪一中数据库管理系统，SQL都可能用

2、关系型数据库：
>建立在关系模型的基础上，由多张相互连接的二维表组成的数据库  

| 姓名 | 电话  |  id  |
| ---- | ---- | ---- |
|      |      |   1  |
|      |      |   2  | 
|      |      |   3  | 

_id对应另一个表_ 

|  id  |  部门  |
| ---- | ----|
| 2 | |
| 3 | |
| 1 | |  

非关系型数据库（NoSQL）：
>不同于传统关系型数据库，突破了结构化数据模型的限制，采取键值对、文档、列家族或图等非结构化方式存储数据，适用大数据、高并发、实时数据等现代化应用场景的需求  （注：二者NoSQL不太理解，只是知道个概念，待补充;之后的内容与关系型数据库管理系统MySQL有关）

3、数据模型（关系型）
首先，明确三个对象：客户端、DBMS（数据库管理系统）、数据库
其次，要注意一点，数据库指的是一个存了多张表以及表表之间关系的仓库，可有多个
然后，三者的关系如下：
> - 客户端连接DBMS  
> - DBMS，即数据库管理系统负责操纵、管理、维护数据库  
> - 对已有的数据库，DBMS可以对其进行操作，创建新表、更新表中数据等等  
> - DBMS可以创建新的数据库  
> - DBMS对数据库的操作通过SQL实现

### 二、SQL
1、通用语法  
> - SQL语句可以单行或多行书写，以分号结尾
> - SQL语句可以使用空格/缩进来增强语句的可读性
> - MySQL中的SQL语句不分大小写
> - 单行注释用--或#，多行用/**/  

2、分类  
> - DDL data defination language 用于定义数据库、表、字段
> - DML data manipulation language 用于增删改数据
> - DQL data query language 用于查询
> - DCL data control language 用于数据库用户控制访问权限


## MySQL的启动与停止

下列指令均在命令行窗口执行  
1、启动
```shell
net start mysql80
# 注：mysql80是在安装MySQL时设置的用户名
```

2、停止
```shell
net stop mysql80
```

3、 客户端连接  
（1）MySQL提供的客户端命令行工具  
（2）系统自带的命令行工具（需要配置环境变量）
> > ```shell
> > mysql -u root -p
> > # 注：后会提示输入密码
> > ```


## DDL语句

### 一、数据库  
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


### 二、表操作-查询

### 三、表操作-创建

### 四、数据类型

### 五、表操作-修改


## DML语句
### 一、添加数据

### 二、修改数据

### 三、删除数据


## DQL语句

> 基本语法

### 一、基本查询

### 二、条件查询

### 三、聚合函数

### 四、分组查询

### 五、排序查询

### 六、分页查询

### 七、DQL语句的执行顺序


## DCL语句

### 一、管理用户

### 二、权限控制


## 函数

### 一、字符串函数

### 二、数值函数

### 三、日期函数

### 四、流程函数


## 约束

### 一、常见约束分类

### 二、添加外键的两种方式

1、创建表时添加  

2、创建表后添加  

3、删除外键  

4、外键约束中的删除/更新  


## 多表查询
> 多表关系
>> - 一对多/多对一
>> - 多对多
>> - 一对一

### 一、一对多

### 二、多对多

### 三、一对一

### 四、多表查询
1、连接查询  
（1）内连接  
（2）外连接  
（3）自连接

2、联合查询

3、子查询


## 事务


