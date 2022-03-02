# Docker
Docker

## 1. Installing Docker

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
>> 5. __Add `cloud_user` to the `docker` group:__
```shell
sudo usermod -aG docker cloud_user
```
