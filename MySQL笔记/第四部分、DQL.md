# DQL语句

> **基本语法**
```mysql
SELECT
      字段列表
FROM
      表名列表
WHERE
      条件列表
GROUP BY
      分组字段列表
HAVING
      分组后条件列表
ORDER BY
      排序字段列表
LIMIT
      分页参数
```
> > 执行顺序或者说判断顺序按上述写法从上往下



## 一、基本查询

> - 基本   
```mysql
SELECT 字段1, 字段2 ··· FROM 表名;
SELECT * FROM 表名;
```

> - 设置别名  
```mysql
SELECT 字段1[AS 别名], 字段2[AS 别名] ··· FROM 表名;
```

> - 去除重复记录  
```mysql
SELECT DISTINCT 字段列表 FROM 表名;
```

## 二、条件查询

```mysql
SELECT 字段列表 FROM 表名 WHERE 条件列表;
```
> - 关于条件
> > 1、比较：>、>=、<、<=、=、<>/!=、BETWEEN···AND···、IN(···)（属于某一列表中的值）、IS NULL  
> > 2、逻辑：AND/&&、OR/||、NOT/！  
> > 3、模糊匹配：‘_’（下划线）代表单个字符，使用时利用LIKE进行匹配，而‘%’代表任意个字符  
```mysql
select * from 表 where 某字段 like  '__'; # 找某字段占了两个字符的xxx信息
select * from 表 where 某字段 like  '___X'; # 找某字段最后一位为X的信息或可以变一下换成查找某一位为X的信息
```

## 三、聚合函数  

**聚合函数即将某一列作为整体进行纵向的计算**  
常见的聚合函数有：count、max、min、avg、sum等等  
```mysql
SELECT 聚合函数(字段列表) FROM 表名; 
```

## 四、分组查询

```mysql
SELECT 字段列表 FROM 表名 WHERE 条件
GROUP BY 分组字段名 HAVING 分组后过滤条件;
```
> - **分清其中的两处条件**  
> > WHERE在分组前过滤，不满足where条件不参与分组，且不能用聚合函数进行判断  
> > HAVING在分组后对结果进行过滤，可以对聚合函数进行判断  

## 五、排序查询

```mysql
SELECT 字段列表 FROM 表名 ORDER BY 字段1 排序方式1, 字段2 排序方式2;
```
> - 排序方式  
> > **ASC(升序)、DESC(降序)**
> > 多字段排序时，当第一个字段值相同时，才会对根据第二个字段进行排序  

## 六、分页查询

```mysql
SELECT 字段列表 FROM 表名 LIMIT 起始索引, 查询记录数;
```
> - **分页查询**注
> > 起始索引从0开始/起始索引=（查询页码-1）*每页显示记录数
> > 分页查询在不同数据库管理系统中有不同的体现，MYSQL时LIMIT  
> > 若查询的时第一页数据，起始索引可以省略  

## 七、例

```mysql
# 查询表中所有数据
select * from emp;

#  查询表中不重复的workaddress数据
select distinct workaddress from emp;

# 条件查询
select id, workno, name, gender, age, idcard, workaddress, entrydate from emp where age = 29;

select id, workno, name, gender, age, idcard, workaddress, entrydate from emp where age >= 36;

select id, workno, name, gender, age, idcard, workaddress, entrydate from emp where idcard is null;

select id, workno, name, gender, age, idcard, workaddress, entrydate from emp where !(idcard is null);

select id, workno, name, gender, age, idcard, workaddress, entrydate from emp where age between 30 and 50;

select id, workno, name, age, idcard from emp where (age between 20 and 60) and (gender = '女');

select id, workno, name, gender, age, idcard, workaddress, entrydate from emp where name like '____';

# 聚合函数的应用
select count(*) from emp;

select gender, count(*) from emp group by gender;

select gender, avg(age) as '年龄' from emp group by gender;

select workaddress, count(workaddress) as '工作地址数量' from emp where age >20 group by workaddress having count(workaddress)>3;

# 排序
select * from emp order by age asc;

select * from emp order by entrydate desc;

select * from emp order by age asc, entrydate desc;

# 分页查询
select * from emp limit 10;# 查询第一页

select * from emp limit 10, 10;

select * from emp where gender = '男' and (age between 20 and 40) order by age, entrydate desc limit 0, 5;

```
