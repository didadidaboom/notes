```
docker pull nacos/nacos-server:1.2.0

docker run --env MODE=standalone --name nacos --restart=always  -d -p 8848:8848 nacos/nacos-server:1.2.0

登陆
http:/ip:8848/nacos

```
