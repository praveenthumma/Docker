# Port-Forwarding


```shell
# run apache webserver container mappping port using -p flag where host-port:container-port
docker run -p 8080:80 -d httpd
curl 10.0.0.4:8080
curl localhost:8080

# run apache webserver container mappping another port using -p flag where host-port:container-port
 
docker run -p 8081:80  --name web2 -d httpd
docker exec -it web2 bash
echo "HEllo Amdocs again" > htdocs/index.html
curl localhost:8080
curl localhost:8081


```
