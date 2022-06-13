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