# Docker
Docker

## 1. Installing Docker on CentOS 7

> - Uninstall old versions:
```shell
sudo yum remove -y docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine

```

> - Install Docker Steps
>> 1. __Add the Utilities needed for Docker:__
```shell
sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
```
>> 2. __Set up the `stable` repository:__
```shell
 sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```
>> 3. __Install Docker CE:__
```shell
sudo yum -y install docker-ce
```
>> 4. __Enable and start Docker:__

```shell
sudo systemctl start docker && sudo systemctl enable docker
```

>> 5 __Verify that Docker Engine is installed correctly by running the hello-world image.__

```shell
sudo docker run hello-world
```
>> __Output__
```
 Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
2db29710123e: Pull complete 
Digest: sha256:97a379f4f88575512824f3b352bc03cd75e239179eea0fecc38e597b2209f49a
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```
>> 6. __Add `cloud_user` to the `docker` group:__
```shell
sudo usermod -aG docker cloud_user
```
