# VMware setting

+ inside of centos 7 : network

  ```shell
  vim etc/sysconfig/network-scripts/ifcfg-ens33
  
  BOOTPROTO="static"
  BROADCAST=192.168.19.255
  IPADDR=192.168.19.137
  NETMASK=255.255.255.0
  GATEWAY=192.168.19.2
  DNS1=192.168.19.2
  ```

  

+ centos 7 setting

  ~~~shell
  自定义 VMnet8
  ~~~

  

+ VMware edit

  ```shell
  VMnet8
  ip:192.168.19.0
  click "NAT setting"
  IP: 192.168.19.2
  APPLY AND CONFIRM
  ```

+ local machine

  ~~~
  网络连接
  VMware Network Adapter-VMnet8
  属性-internet协议版本4（TCP/IPv4）
  ip:192.168.19.1
  子网掩码: 255.255.255.0
  默认网关:192.168.19.2
  ~~~

  

+ test (inside of centos 7)

  ~~~shell
  ping 192.169.19.1
  ~~~

  

+ 