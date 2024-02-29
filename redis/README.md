# Redis

```shell
sudo apt search redis
sudo apt-get update
sudo apt-get install redis-server
```

```shell
# set dameon process
# sudo vim /usr/bin/redis-server/redis.conf
daemonize yes
./redis-server &
```

```shell
# docker
sudo docker run -itd \
    --name redis \
    -p 6379:6379 \
    redis:latest \
    --requirepass 'your-password'
```
