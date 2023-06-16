```
yum upgrade
yum install net-tools
```

^51c2ae

####安装apache  
关闭SELinux  
编辑器打开 etc/selinux/config 文件，找到 SELINUX=enforcing 字段，将其改成 SELINUX=disabled ，并重启设备。  
yum -y install httpd mod_ssl  
配置防火墙  
firewall-cmd --permanent --add-port=80/tcp  
firewall-cmd --permanent --add-port=443/tcp  
firewall-cmd --reload

```
<VirtualHost *:81>
    DocumentRoot /var/www/web/
    DirectoryIndex index.html index.php
    #ServerName localhost:81
    <Directory "/var/www/web">
        Options FollowSymLinks
        AllowOverride None
        Order allow,deny
        Allow from all
        Header set Access-Control-Allow-Origin *
    </Directory>
</VirtualHost>

开机启动
systemctl start httpd
systemctl enable httpd
终端输入如下指令检查httpd的运行状态
sudo systemctl status httpd
```

####安装PHP7

- 添加源

```shell
rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm

当https不可用时可以改用http
把/etc/yum.repos.d目录下epel.repo和webtatic.repo文件中https改为http
```

- 安装

```shell
yum install php70w php70w-common php70w-fpm php70w-opcache php70w-gd php70w-mysqlnd php70w-mbstring php70w-pecl-redis php70w-pecl-memcached php70w-devel
```

####安装mysql5.7

```
1.安装wget
	yum -y install wget
2.安装源
	wget http://dev.mysql.com/get/mysql57-community-release-el7-8.noarch.rpm
	rpm -ivh mysql57-community-release-el7-8.noarch.rpm
3.安装mysql
	yum install mysql-server
4.启动mysql服务
	systemctl start mysqld
5.查看MySQL的启动状态
	systemctl status mysqld
6.开机启动
	systemctl enable mysqld
	systemctl daemon-reload
7.修改root本地登录密码
	查找mysql生成的随机密码
	grep 'temporary password' /var/log/mysqld.log
	mysql -uroot -p
	修改密码，注意：mysql5.7默认安装了密码安全检查插件（validate_password），默认密码检查策略要求密码必须包含：大小写字母、数字和特殊符号，并且长度不能少于8位。否则会提示ERROR 1819 (HY000): Your password does not satisfy the current policy requirements错误
	ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyNewPass4!'; 
	
8.配置默认编码为utf8
	修改/etc/my.cnf配置文件，在[mysqld]下添加编码配置
	[mysqld]
	character_set_server=utf8
	init_connect='SET NAMES utf8'
9.配置mysql远程连接
	mysql -uroot -p
	use mysql;
	Grant all on *.* to 'root'@'%' identified by 'root用户的密码' with grant option;
flush privileges;
然后用以下命令查看哪些用户和host可以访问，%代表任意ip地址
select user,host from user;
防火墙添加3306端口
firewall-cmd --zone=public --add-port=3306/tcp --permanent
firewall-cmd --reload

禁止远程访问
my.cnf 中添加以下配置
# The TCP/IP Port the MySQL Server will listen on
port=3306
bind-address=127.0.0.1

10.mysql忘记密码

1.修改MySQL的配置文件（默认为/etc/my.cnf）,在[mysqld]下添加一行skip-grant-tables
2.service mysqld restart后，即可直接用mysql进入
3.mysql> update mysql.user set authentication_string=password('123qwe') where user='root' and Host = 'localhost';
   mysql> flush privileges;
   mysql> quit;
 将/etc/my.cnf文件还原，重新启动mysql:service mysql restart,这个时候可以使用mysql -u root -p'123qwe'进入了
 
 mysql>SET PASSWORD = PASSWORD('newpasswd'); 设置新密码
```

文章知识点与官方知识档案匹配，可进一步学习相关知识