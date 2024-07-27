# Redis

Redis can be used as a database, cache, streaming engine, message broker, and more.

## Install

```shell
sudo apt search redis
sudo apt-get update
sudo apt-get install redis-server

# docker recommended
sudo docker run -itd \
    --name redis \
    -p 6379:6379 \
    redis:latest \
    --requirepass 'your-password'
```

## Dameon process

```shell
# set dameon process
# sudo vim /usr/bin/redis-server/redis.conf
daemonize yes
./redis-server &
```
