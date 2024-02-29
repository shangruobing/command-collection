# MySQL

```shell
sudo apt-get install mysql-server
# 连接服务
sudo mysql -u root -p
show databases;
create database nfqa;
use nfqa;
mysql> source /home/NFQA/data/nfqa.sql;

service mysql status
service mysql start
service mysql stop
```

## Exit
```Shell
quit
select user,authentication_string from user where user='root';
update user set authentication_string='123456' where user='root';

create user 'django-user'@'localhost' identified by '123456';
grant usage on *.* to 'django-user'@'localhost';
grant all privileges on nfqa.* to 'django-user'@'localhost';
```

## Remote Connection

1. 查看数据库服务是否启动`systemctl status mysql`
2. 查看数据库端口是否为3306`show global variables like 'port';`
3. 查看root用户权限，%代表允许所有连接`SELECT user,host FROM mysql.user;`
4. 查看配置文件mysqld.conf的bind_address地址是否为0.0.0.0

> 配置文件路径 /etc/mysql/mysql.conf.d/mysqld.cnf

## Set Password

```shell
# 进入MySQL命令行
sudo mysql -u root
# 使用mysql数据库
use mysql;

create user 'admin'@'localhost';
# 查看root的密码插件是否为auth_socket;是则需要更改,否则密码无效
SELECT User, Host, plugin FROM mysql.user;
UPDATE user SET plugin='mysql_native_password' WHERE User = 'admin';
UPDATE user SET plugin='caching_sha2_password' WHERE User = 'root';
# 刷新权限
FLUSH PRIVILEGES;
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%';
# 重启服务
sudo service mysql restart;
# 修改密码
ALTER USER 'admin'@'%' IDENTIFIED WITH mysql_native_password BY 'your_password';
# 二选一,推荐第一种
update mysql.user set authentication_string=password('123456') where user='root';
```