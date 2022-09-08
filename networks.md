# Docker Network


```shell

brctl show docker0

# Lsit all docker networks

docker network ls
ip a
mkdir netimg
cd netimg


vi Dockerfile
FROM ubuntu:18.04
RUN apt-get update  && apt-get install -y iputils-ping traceroute
ENTRYPOINT ["/bin/bash"]

docker build -t="netimg" .

# Create a docker network n1 
docker network create n1

# run container in the newly created network 
docker run --network n1 --name=net1  -it netimg

ping google.com
ping 10.0.0.4 


#Try to ping any other container ip address outside n1
ping 172.17.0.2
# Above ping will fail

# gracefully exit from bash without closing
Ctl+P+Q


# run another container in the newly created network 
docker run --network n1 --name=net2 -it netimg

# ping the net1 ipaddress which is from same n/w

ping 172.18.0.2
# Above should succeed and should response
ping 172.17.0.2
# ping the net1 hostname which is from same n/w
ping net1

# gracefully exit from bash without closing

Ctl+P+Q
# open bash in net1
docker exec -it net1 bash

# ping net2 from nte1
ping net2
traceroute  8.8.8.8


```
