

```shell
# ubuntu 22 下 6.0
sudo apt-get install redis-server 
ps -ef | grep redis  

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



```redis
keys *
```
















