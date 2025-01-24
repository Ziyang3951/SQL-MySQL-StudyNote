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

## 三、表操作-创建

## 四、数据类型

## 五、表操作-修改
