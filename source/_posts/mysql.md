---
title: mysql
date: 2019-08-25 14:46:27
tags:
    - mysql7
    - 数据安装
    - sql
---
## Mysql 命令
```cmd
desc table；  #显示表头
select Host,User,plugin from user;  #用户名，登录方式，用户名，认证方式，
ALTER USER root@localhost IDENTIFIED WITH mysql_native_password BY 'root';  #修改root认证方式mysql_native_password，密码为root
FLUSH PRIVILEGES;  #刷新认证表
set password for root@localhost = password('root');   #修改密码
UPDATE user SET Password=PASSWORD('newpassword') where USER='root';   #修改密码
ALTER USER root@localhost identified WITH mysql_native_password BY 'root';  #修改密码
```
## Mysql5.7解压版cmd命令安装
```cmd
解压目录下新建  my.ini  文件，内容如下
----------
[mysqld]
port= 3306                      #服务器端口
basedir="D:/path/mysql7"        #安装目录（因人而异）
datadir="D:/path/mysql7/data"   #数据保存位置（必须存在，不然报错）
max_connections=200
character-set-server=utf8
default-storage-engine=INNODB
sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES
[mysql]
default-character-set=utf8
----------
在解压目录bin下启动cmd（管理员权限）
mysqld --initialize-insecure  #初始化无密码数据库
mysqld --install  sql7  #安装服务，服务名为 sql7（个人喜好）
net start sql7           #开启数据库 提示成功，表示安装成功
```