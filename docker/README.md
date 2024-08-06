# Docker

Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. By taking advantage of Docker's methodologies for shipping, testing, and deploying code, you can significantly reduce the delay between writing code and running it in production.

## Install

```shell
# Install Docker
sudo apt install -y docker.io

# Register Docker as a service
sudo systemctl start docker
sudo systemctl enable docker

# Check the version
sudo docker version
```

## Build

```shell
sudo docker build -t imagename:0.0.1 .
# Build for ARM
sudo docker build --platform linux/amd64 -t imagename:0.0.1 .
```

## Run

```shell
# -d deamon
# 8080:8080 host port:docker container port
sudo docker run -itd --name containername -p 8080:8080 imagename:0.0.1
```

## Publish and Download

```shell
# Login and push image to Dockerhub
sudo docker login
sudo docker tag imagename:0.0.1 username/repository:imagename-0.0.1
sudo docker push username/repository:imagename-0.0.1

# Download image from Dockerhub
sudo docker pull username/repository:imagename-0.0.1

sudo docker run -itd \
  --name containername-0.0.1 \
  -p 8080:8080 \
  username/repository:imagename-0.0.1
```

## Common

```shell
# List all containers
sudo docker ps -a

# Remove all containers
sudo docker rm -f $(sudo docker ps -aq)

# Remove images
sudo docker rmi -f $(sudo docker images -q "username/re po:imagename-*")

# List all images
sudo docker images

# Remove image by Id
sudo docker rmi -f image_id

# View the container log
sudo docker logs -f container_id

# Execute the container program
sudo docker exec -it container_id /bin/sh
sudo docker exec -it container_name /bin/sh

# Copy files from container to host
sudo docker cp container_name:/upload /home/ubuntu/upload

# Start and restart container
sudo docker start container_name
sudo docker restart container_name

# Offline package the image
sudo docker save -o filename.tar image_name

# Load a image from the offline package
sudo docker load -i filename.tar
```

## Volume

```shell
sudo docker volume create volume-name
```

## Docker Building Error

> ERROR [internal] load metadata for docker.io

```shell
docker logout
docker login
```

Modify the `credsStore` in `/Users/Username/.docker/config.json `

```json
# .docker/config.json
{
	"auths": {
		"https://index.docker.io/v1/": {}
	},
	"credsStore": "osxkeychain",
	"currentContext": "desktop-linux",
	"plugins": {
		"-x-cli-hints": {
			"enabled": "true"
		}
	}
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
