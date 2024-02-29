# Docker

## Install

```shell
# 安装启动Docker
sudo apt install -y docker.io
# 注册docker为服务
sudo systemctl start docker
sudo systemctl enable docker
sudo docker version
```

## Build

```shell
# 当前平台打包
sudo docker build -t imagename:0.0.1 .
# 指定平台打包
sudo docker build --platform linux/amd64 -t imagename:0.0.1 .
```

## Run

```shell
# -d表示deamon,守护进程后台执行; 8080:8080 主机端口:docker端口
sudo docker run -itd --name containername -p 8080:8080 imagename:0.0.1
```

## Publish and Download

```shell
# 登录帐号推送至Dockerhub
sudo docker login
sudo docker tag imagename:0.0.1 username/org:imagename-0.0.1
sudo docker push username/org:imagename-0.0.1

# 从Dockerhub下载image并运行
sudo docker pull username/org:imagename-0.0.1

sudo docker run -itd \
  --name containername-0.0.1 \
  -p 8080:8080 \
  username/org:imagename-0.0.1
```

## Common

```shell
# 列出所有容器
sudo docker ps -a
# 删除所有容器
sudo docker rm -f $(sudo docker ps -aq)
# 列出所有镜像
sudo docker images
# 根据Id删除镜像
sudo docker rmi -f container_id
# 根据Id查看镜像日志
sudo docker logs -f container_id
# 根据Id进入到容器到bash或sh
sudo docker exec -it container_id /bin/sh
sudo docker exec -it container_name /bin/sh
# 将容器内的数据拷贝到主机
sudo docker cp container_name:/upload /home/ubuntu/upload
```

## Volume

```shell
sudo docker volume create volume-name
```

## Docker 打包出错

> ERROR [internal] load metadata for docker.io
> 将/Users/Username/.docker/config.json 下的 credsStore 改为 credStore

```json
{
  //"credsStore": "desktop"
  "credStore": "desktop"
}
```

## Example

```shell
sudo docker run -itd --name "container_name" \
  -p 8020:8020 \
  -e SPRING_PROFILES_ACTIVE=prod \
  -v /home/ubuntu/project/upload:/upload \
  -v /home/ubuntu/project/template:/template \
  "image_name"
```
