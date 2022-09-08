# Docker Volumes

## Volumes basics

```shell
docker volume ls

# Create a volume db vol

docker volume create dbvol

# list all volumes in docker
docker volume ls

# Inspect a volume
docker volume inspect dbvol

#create a mysql container with the volume mounted 

docker run --name db1 -e MYSQL_ROOT_PASSWORD=root -d -v dbvol:/var/lib/mysql mysql
docker ps

#log into the mysql box
docker exec -it db1 bash
mysql -u root -proot
create database db1;
use db1;
create table employee(id int, name varchar(30));
insert into employee(id, name) values(1, "sai");
insert into employee(id, name) values(2, "shiva");
insert into employee(id, name) values(3, "natarajan");
select * from employee;
exit
exit

# remove the mysql container
docker rm --force db1
docker ps
docker volume ls
 
 
#create another mysql container amd mount the previously created volume
 
docker run --name db2 -e MYSQL_ROOT_PASSWORD=root -d -v dbvol:/var/lib/mysql mysql
docker ps
docker exec -it db2 bash
mysql -u root -proot
use db1;

# check the table created using the earlier container ,
select * from employee;

docker rm --force db2
docker volume rm db1
docker volume ls

```

## Mounting Volumes from host machine

```shell
mkdir voldir
echo "Volumes are awesome" > voldir/data.txt

# mount local dir to volume and run docker container and open bash
docker run -v /home/azureuser/voldir:/vol1 -it ubuntu:18.04 bash
ls /
ls /vol1
cat /vol1/data.txt

# Create files inside mounted volume

echo "THis is awesome too" >> /vol1/data.txt
cat /vol1/data.txt
echo "Another awesome" > /vol1/fromcontainer.txt
ls /vol1
exit

# Check files created from container in host directory
cat voldir/fromcontainer.txt

docker volume ls

echo "Awesome Amdocs" > voldir/index.html

# mount storage to a docker container (apache webserver from local directory)

docker run -v /home/azureuser/voldir:/usr/local/apache2/htdocs/ --name web1 -d httpd
docker inspect web1
docker inspect web1 | grep IPAddress
# curl 172.17.0.2
curl IPAddress
curl 172.17.0.2/data.txt
```
