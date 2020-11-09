[toc]

#### 1. 数据库配置

sudo apt install mariadb-server

修改监听地址

vim /etc/mysql/mariadb.conf.d/50-server.cnf

```
#bind-address            = 127.0.0.1
```

sudo service mariadb start



sudo mysql -uroot

```
grant all privileges on *.* to root@'localhost' identified by '密码';
flush privileges;
```



```
create database foodie-shop-dev default character SET utf8mb4 collate utf8mb4_general_ci; 
show databases;
use foodie-shop-dev;
source <path>/foodie-shop-dev.sql
show tabelse;
```

