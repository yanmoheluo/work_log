  1、根据官网提供的方法登录连接到EC2服务器（[ssh](https://so.csdn.net/so/search?q=ssh&spm=1001.2101.3001.7020)连接）

    2、 创建root的密码，输入如下命令： sudo passwd root  

    3、然后会提示你输入new password。输入一个你要设置的root的密码，需要你再输入一遍进行验证。

    4、接下来，切换到root身份，输入如下命令：su root

密码

5.修改ssh配置文件，允许密码登录

 vi /etc/ssh/sshd_config 

a。将 PasswordAuthentication no 改为  PasswordAuthentication yes

b。将 PermitRootLogin 改为yes

6 重启 systemctl restart sshd.service   这是centos7版本

一定要在密码登陆成功的情况下，再禁用秘钥登陆，否则你就再也进不去系统了，一定！！！！！！！

1、修改配置文件CentOS7配置SFTP

vim /etc/ssh/sshd_config  
##下面这行注释掉  
#Subsystem sftp /usr/libexec/openssh/sftp-server  
##后面加入  
Subsystem sftp internal-sftp

2、重启 systemctl restart sshd.service   这是centos7版本  
 

====================================================================

[aws](https://so.csdn.net/so/search?q=aws&spm=1001.2101.3001.7020)的rds和redis安全组选择对应的ec2实例的安全组 ，打开相应私有ip的端口 

远程连接redis

redis-cli -h 地址 -p 6379

远程连接MySQL

mysql  -h 地址 -P 3306 -u账号 -p