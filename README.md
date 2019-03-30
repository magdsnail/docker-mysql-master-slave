### docker 部署mysql 主从<br/>
![图示](https://github.com/magdsnail/docker-mysql-master-slave/blob/master/images/mysql-gtid.jpg)
##### 实例为一主一从可酌情增加<br/>
##### 根据docker-compose.yml注释 选择备份规范 conf为mysql配置文件
##### 启动方式 docker-compose
#### 重要的

##### CREATE USER 'repl'@'%' IDENTIFIED BY 'password';
##### GRANT REPLICATION SLAVE ON *.* TO 'repl'@'%';

##### show master status;
##### binlog CHANGE MASTER TO MASTER_HOST='mysqlmb', MASTER_USER='repl', MASTER_PASSWORD='repl', MASTER_LOG_FILE='binlog.000004', MASTER_LOG_POS=155;
#### or
##### CHANGE MASTER TO MASTER_HOST = 'mysqlmb',MASTER_PORT = 3306,MASTER_USER = 'repl',MASTER_PASSWORD = 'repl',MASTER_AUTO_POSITION = 1;
##### SET @@GLOBAL.read_only = ON;
#### start slave; show slave status \G
https://dev.mysql.com/doc/refman/8.0/en/replication.html<br/>
https://dev.mysql.com/doc/refman/8.0/en/replication-gtids-howto.html<br/>
https://www.hi-linux.com/posts/47176.html


