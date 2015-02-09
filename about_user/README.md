##用户相关

### 创建数据库

```sql
CREATE DATABASE `testDb` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
```
### 创建用户

创建一个用户名为godsee,密码为123456：

```sql
//创建
create user godsee identified by '123456';

//授权godsee使用localhost，对testDb数据所有权限
grant all privileges on testDb.* to 'godsee'@'localhost' identified by '123456';

//刷新权限表
flush privileges;
```

### 删除用户

```sql
DROP USER godsee
flush privileges;
```

### 更新密码

最方便的当然是使用phpmysql修改密码，但有时候也需要命令行。先登录数据库，然后使用如下命令删除:

```sql
SET PASSWORD FOR username@"%" = PASSWORD('password');
```
或者对用户重新授权操作:

```sql
GRANT USAGE ON *.* TO username@"%" IDENTIFIED BY 'password';
```
username,password因实际情况不同自行更换即可。

### 更改用户名

```sql
use mysql;
update user set user="new userName" where user="old userName";
flush privileges;
\q;
```
