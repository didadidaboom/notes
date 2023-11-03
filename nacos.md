```
docker pull nacos/nacos-server:1.2.0

docker run --env MODE=standalone --name nacos --restart=always -d -p 8848:8848 nacos/nacos-server:1.2.0

登陆
http:/ip:8848/nacos

登陆设置
docker exec -it nacos /bin/bash
cd conf/
vim application.properties
修改
nacos.core.auth.enabled=true
nacos.core.auth.enabled.userAgentAuthWhite=false
```
