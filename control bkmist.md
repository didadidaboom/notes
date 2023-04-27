# control bkmist

+ start virtual environment

  ~~~shell
  source ~/project/bkmist/env_bkmist/bin/activate
  ~~~

+ uwsgi

  ~~~shell
  cd /home/ubuntu/project/bkmist/bkmist_git/Ant_api
  # start
  uwsgi --ini xxx.ini  #django-uwsgi.ini
  # stop
  uwsgi --stop xxx.pid
  
  # check uwsgi process
  ps aux|grep uwsgi
  # kill pid
  kill -9 portnum
  ~~~

+ nginx

  ~~~shell
  sudo su
  sudo -i #quit or ctrl+D
  # start
  cd /etc/nginx
  nginx
  sudo service nginx start
  # stop 
  cd /usr/local/nginx/sbin
  ./nignx -s stop
  # remove log
  rm /var/log/nginx/*
  # force to stop
  kill -9 nginx
  # check nginx process
  ps -aux | grep nginx
  #
  ~~~

  

+ 
