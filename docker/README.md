# Docker

## Install

```shell
# 安装启动Docker
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
sudo docker version
```

## Build

```shell
# 当前平台打包
sudo docker build -t fundsearch:0.0.1 .
# 指定平台打包
sudo docker buildx build --platform linux/amd64 -t fundsearch:0.0.1 .
```

## Run

```shell
#  -d表示deamon,守护进程后台执行; 8080:8080 主机端口:docker端口
sudo docker run -itd --name fundsearch -p 8080:8080 fundsearch:0.0.1
```

## Publish and Download

```shell
# 登录后push到Dockerhub
sudo docker login
sudo docker tag fundsearch:0.0.1 shangruobing/huanxiongjia:fundsearch-remote-0.0.1
sudo docker push shangruobing/huanxiongjia:fundsearch-remote-0.0.1

# 从Dockerhub下载image并运行
sudo docker pull shangruobing/huanxiongjia:fundsearch-remote-0.0.1
sudo docker run -itd --name fundsearch-remote-0.0.1 -p 8080:8080 shangruobing/huanxiongjia:fundsearch-remote-0.0.1
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
sudo docker rmi 21f32ab04934 -f
# 根据Id查看镜像日志
sudo docker logs -f 72f9392cf4cb
# 根据Id进入到容器到bash或sh
sudo docker exec -it 72f9392cf4cb /bin/sh
sudo docker exec -it red-packet-remote-dev /bin/sh
# 将容器内的数据拷贝到主机
sudo docker cp red-packet-remote-dev:/upload /home/ubuntu/redpacket
```

## Volume

```shell
sudo docker volume create red-packet-volume
```

## Docker打包出错

> ERROR [internal] load metadata for docker.io
> 将/Users/Username/.docker/config.json下的credsStore改为credStore

```json5
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
  -v /home/ubuntu/redpacket/upload:/upload \
  -v /home/ubuntu/redpacket/template:/template \
  "image_name"
```