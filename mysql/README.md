# MySQL

MySQL is a popular open-source relational database management system (RDBMS). It is widely used for storing, retrieving, and managing data in various types of applications, from web development to enterprise software. MySQL uses SQL (Structured Query Language), a standard language for interacting with relational databases.

```shell
# Install
sudo apt-get install mysql-server

# Connect the MySQL shell
sudo mysql -u root -p

show databases;
create database yourdb;
use yourdb;

# Execute sql file
mysql> source /home/data/yourdb.sql;

service mysql status
service mysql start
service mysql stop
```

## Remote Connection

1. Check the service status `systemctl status mysql`
2. Check the database port is 3306 `show global variables like 'port';`
3. Check `root` permission ，`%` means allow all connection `SELECT user,host FROM mysql.user;`
4. Check the configuration `mysqld.conf` `bind_address` is `0.0.0.0`

> configuration file path /etc/mysql/mysql.conf.d/mysqld.cnf

## Set Password

```shell
# Connect the MySQL shell
sudo mysql -u root

# Use MySQL database
use mysql;

create user 'admin'@'localhost';

# Check the root user password plugin whether auth_socket
SELECT User, Host, plugin FROM mysql.user;

# Change the root user password plugin
UPDATE user SET plugin='mysql_native_password' WHERE User = 'admin';
UPDATE user SET plugin='caching_sha2_password' WHERE User = 'root';

# Flush privileges
FLUSH PRIVILEGES;
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%';

# Restart the MySQL service
sudo service mysql restart;

# Update the password
ALTER USER 'admin'@'%' IDENTIFIED WITH mysql_native_password BY 'your_password';
# Update the password
UPDATE mysql.user set authentication_string=password('123456') where user='root';
```
