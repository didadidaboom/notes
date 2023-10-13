# mysql

+ change mode

  ```sql
  #check mode
  show variables like "sql_mode";
  # set mode
  SET sql_mode='STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION';
  ```

+ 远程连接

  ~~~shell
  sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
  
  bind-address 127.0.0.1  # 改为 
  bind-address 0.0.0.0
  #noted：在某些 MySQL 版本的配置文件中，没有 bind - address #这一行，这种情况下，在合适的位置加上就可以了
  save
  
  sudo systemctl restart mysql
  ~~~
   
+
 grant all on database_name.* TO 'username'@'%' with grant option;

+ docker 运行mysql
```
#首先需要创建将要映射到容器中的目录以及.cnf文件，然后再创建容器
mkdir -p docker_v/mysql/conf
cd docker_v/mysql/conf
touch my.conf
#注意端口，前者为linux端口，后者为容器中的端口
docker run -p 3306:3306 --name mysql -v /opt/docker_v/mysql/conf:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=123456 -d imageID

docker run -p 3306:3306 --name mysql -v /opt/mysql/conf:/etc/mysql -v /opt/mysql/logs:/var/log/mysql -v /opt/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -d imageID

#进入运行中的mysql容器
docker exec -it container_id /bin/bash
#登陆mysql 并用创建容器的密码
mysql -u root -p
#运行远程连接，而不是localhost而已
alter user 'root'@'%' identified with mysql_native_password by '123456';
``` 
