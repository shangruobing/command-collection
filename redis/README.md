# Redis

```shell
sudo apt search redis
sudo apt-get update
sudo apt-get install redis-server
/usr/bin/redis-server

redis.conf设置守护进程
daemonize yes 
./redis-server &
```

```shell
sudo docker run -itd --name redis -p 6379:6379 redis:latest --requirepass 'your-password'
```