
```
docker pull redis

mkdir -p /docker-data/redis

cd /docker-data/redis

wget http://download.redis.io/redis-stable/redis.conf

chmod 777 ~/docker-data/redis
sudo chown -R $USER redis.conf

vi /docker-data/redis/redis.conf

#bind 127.0.0.1 # 这行要注释掉，解除本地连接限制
protected-mode no # 默认yes，如果设置为yes，则只允许在本机的回环连接，其他机器无法连接。
daemonize no # 默认no 为不守护进程模式，docker部署不需要改为yes，docker run -d本身就是后台启动，不然会冲突
requirepass 123456 # 设置密码 前面不能有空格
appendonly yes # 持久化

docker run --name redis-gotyouapp -p 6379:6379 -v /docker-data/redis/redis.conf:/etc/redis/redis.conf -v /docker-data/redis:/data -d redis redis-server /etc/redis/redis.conf --appendonly yes --requirepass xxxx
```

+ 客户端
  redis desktop manager 
