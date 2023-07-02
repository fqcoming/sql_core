

```shell
# ubuntu 22 下 6.0
sudo apt-get install redis-server 
ps -ef | grep redis  
ps aux | grep redis-server

# 这种方式安装的redis其配置文件放在了/etc/redis/redis.conf

# method 1
redis-server --version

# method 2
redis-cli
INFO SERVER
quit

# install hiredis 
git clone https://github.com/redis/hiredis
cd hiredis
make
sudo make install
sudo ldconfig /usr/local/lib
```



### 一、redis相关命令详解及其原理

#### 1.redis是什么?

Remote Dictionary Service: 远程字典服务
散列表，类似于：unordered_map<string, T>类型
通过TCP与redis建立连接进行交互
请求回应模型
内存数据库：数据一定在内存中存在，但不一定在磁盘中出现，不可能出现数据不在内存中而在磁盘中
数据结构数据库
string: 二进制安全的字符串
list: 循环双向链表
hash: 散列表
zse: 有序集合
set: 集合
stream
hyperloglog
......


#### 2.怎么设计kv?

怎么设计key?
所有的key都是string类型的
单个功能一个key: 取有意义的key名字，比如: id_gen
相同功能多个key: 以:作为分割，比如：role:10001



string

```redis
# key 中加冒号，redis客户端会帮我构建树状结构
set role:10001 100   # role:10001 和 100 都是string类型的
set role:10002 101

```

hash

```
hset roleinfo:10001 age 30     # (integer) 1
hget roleinfo:10001 age
```


list 

```
lpush teacher mark darren king  # (integer) 3
lpop teacher  # "king"
lrange teacher 0 -1

# return
# 1) "darren"
# 2) "mark"

lpush teacher king king
```



zset

```
zadd rank 80 mark  # 80是score mark是member
zadd rank 90 darren
zadd rank 100 king 
zrange rank 0 -1
```


1) "mark"
2) "darren"
3) "king"


```
zadd rank 91 mark
zrange rank 0 -1
```

1) "darren"
2) "mark"
3) "king"



#### 3.redis抽象层次








```redis
keys *


set mark 100

```
















