## sql_core





```shell
cd /etc/mysql/mysql.conf.d/    # mysql.cnf  mysqld.cnf
su root
cd /var/lib/mysql
ls
```

```
 auto.cnf        binlog.000010    '#ib_16384_0.dblwr'   performance_schema
 binlog.000001   binlog.000011    '#ib_16384_1.dblwr'   private_key.pem
 binlog.000002   binlog.000012     ib_buffer_pool       public_key.pem
 binlog.000003   binlog.index      ibdata1              server-cert.pem
 binlog.000004   ca-key.pem        ibtmp1               server-key.pem
 binlog.000005   ca.pem            imshilei.pid         sys
 binlog.000006   chat             '#innodb_redo'        undo_001
 binlog.000007   client-cert.pem  '#innodb_temp'        undo_002
 binlog.000008   client-key.pem    mysql
 binlog.000009   debian-5.7.flag   mysql.ibd

```

```shell
cd chat
ls
```

```
allgroup.ibd  friend.ibd  groupuser.ibd  offlinemessage.ibd  user.ibd
```

`.ibd` 文件是 InnoDB 存储引擎的数据文件之一。InnoDB 存储引擎使用 `.ibd` 文件来存储表的数据和索引。





```shell
service mysql restart
mysql -h 192.168.40.133 -P 3306 -u root -p  # remote login
```



























## sql







```sql
show databases;
show tables;
```



```sql
desc user;
```

```
+-------+--------------+------+-----+---------+-------+
| Field | Type         | Null | Key | Default | Extra |
+-------+--------------+------+-----+---------+-------+
| name  | varchar(255) | YES  |     | NULL    |       |
| age   | int          | YES  |     | NULL    |       |
| sex   | varchar(10)  | YES  |     | NULL    |       |
+-------+--------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```



### limit分页查询详解

```sql
# limit3种语法
select * from user limit 3;  # offset为0，lines为3
select * from user limit 3,3; # offset为3，lines为3
select * from user limit 3 offset 1; # offset为1，lines为3
```







### explain查看SQL语句的执行计划

```sql
explain select * from user where name = 'zhangsan';
```

![image-20230714104058049](doc/image-20230714104058049.png)



show create table user\G























































