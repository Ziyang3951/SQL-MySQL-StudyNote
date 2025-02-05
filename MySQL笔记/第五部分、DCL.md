# DCL语句

## 一、管理用户

> mysql里面有一个表存放了用户信息
```mysql
USE mysql;
```

> - 查询用户
```mysql
SELECT * FROM user;
```

> - 创建用户
```mysql
CREATE USER '用户名'@'主机名' IDENTIFIED BY '密码';
```

> - 修改用户密码
```mysql
ALTER USER '用户名'@'主机名' IDENTIFIED WITH BY mysql_native_password '新密码';
```

## 二、权限控制

> - 常用权限  
|名称 |含义 |
|---|---|
|ALL, ALL PRIVILEGES |所有权限|
|SELECT |查询数据 |
|INSERT |插入数据 |
|UPDATE |修改数据 |
|DELETE |删除数据 |
|ALTER |修改表|
|DROP |删除数据库、表、视图|
|CREATE |创建表、数据库|

> - 查询权限  

```mysql
SHOW GRANTS FOR '用户名'@'主机名';
```

> - 授予权限

```mysql
GRANT 权限列表 ON 数据库名.表名 TO '用户名'@'主机名';
```

> - 撤销权限

```mysql
REMOVE 权限列表 ON 数据库名.表名 FROM '用户名'@'主机名';
```
> > 注：多个权限之间逗号分隔 ；授权时，数据库和表都可以用‘*’表示


## 三、例

```mysql
create user 'boss'@'%' identified by '123456';

alter user 'boss'@'%' identified with mysql_native_password by '1234';

drop user 'itcast'@'localhost';

show grants for 'root'@'localhost';

show grants for 'boss'@'%';

grant all on mydata1.* to 'boss'@'%';

show grants for 'boss'@'%';

revoke all on mydata1.* from 'boss'@'%';

show grants for 'boss'@'%';
```
