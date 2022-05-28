+ docker commands

```shell
sudo systemctl start docker

#查看本地镜像
docker images
#查看运行中的容器
docker ps
docker ps -a
#开启/停止/重启容器
docker stop <container-name>  #关闭
docker kill <container-name>  #强壮关闭
docker start <container-name>  #启动
docker restart <container-name>  #重启

#删除容器
docker rm <container or container-id>
#查看容器详情
docker inspect <container or container-id>


#显示容器硬件资源使用情况
docker stats 

#将容器保存为镜像
docker commit <container or container-id> <image-name>:<tag>

#打包本地镜像，使用压缩包来完成迁移
docker save <image-name> > <data-root>
#导入镜像压缩包
docker load < <文件路径>
#修改镜像tag
docker tag <image-name or image-id> <new-image-name>:<new-tag>

#创建启动容器
docker run <parameters> <image-name or image-id> <command>
-d #后台运行
--name “container-name” #为容器指定一个别名
-p <host-port>:<container-port> #宿主机到容器的端口映射, 可指定宿主机的要监听的 ip, 默认为 0.0.0.0
-v <host-data-root>:<container-data-root>  #挂载宿主机的指定目录 ( 或文件 ) 到容器内的指定目录 ( 或文件 )


#推送镜像到仓库
docker push <image-name>:<tag>
#获取镜像
docker pull <rapo>:<tag>

#进入正在运行的容器内部，同时运行bash
docker exec -t -i <container-name or id> /bin/bash
#查看容器日志 
docker logs

#首先需要创建将要映射到容器中的目录以及.cnf文件，然后再创建容器
mkdir -p docker_v/mysql/conf
cd docker_v/mysql/conf
touch my.conf
docker run -p 3306:3306 --name mysql -v /opt/docker_v/mysql/conf:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=123456 -d imageID

#运行容器mysql
docker run -d --name mysql-test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql
docker run -d --name mysql-test -p 3306:3306  -v /opt/docker/mysq/conf:/etc/mysql/conf.d mysql
设置登录密码
mysql -u root -p
ALTER USER "root"@'localhost' IDENTIFIED BY 'test123';
#添加远程登陆用户
CREATE USER "test"@'%' IDENTIFIED WITH mysql_native_password BY 'test123';
GRANT ALL PRIVILEGES ON  *.* TO 'test'@'%';
```

```shell
#copy file from host to container
docker cp foo.txt container_id:/foo.txt
#copy file from container to host
docker cp container_id:/foo.txt foo.txt

#operate mysql through script
mysql: source foo.txt
```

+ issue - related to entrypoints.sh
  + solved: by specifying latest version of docker 
