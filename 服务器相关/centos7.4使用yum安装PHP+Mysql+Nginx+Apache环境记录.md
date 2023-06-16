## [Nginx](https://so.csdn.net/so/search?q=Nginx&spm=1001.2101.3001.7020) 方法一

1.Nginx安装

```
yum install -y nginx
```

注：检查是否有源 yum search nginx ，如无源，则添加源 `rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm`  
2.启动Nginx

```
systemctl start nginx
```

3.设置开机自动运行

```
systemctl enable nginx
```

wget安装nginx  
#下载:

## Nginx 方法二

```java
wget http://nginx.org/download/nginx-1.8.0.tar.gz
```

#解压:

```java
tar -zxvf nginx-1.8.0.tar.gz
```

#安装依赖插件

```java
yum install -y gcc gcc-c++ ncurses-devel perl pcre pcre-devel zlib gzip zlib-devel
```

#进入目录编译安装

```java
cd nginx-1.8.0

./configure

make && make install
```

## [Apache](https://so.csdn.net/so/search?q=Apache&spm=1001.2101.3001.7020)

1.安装Apache

```
yum install httpd -y
```

2.启动Apache

```
systemctl start httpd
```

3.设置开机自动运行Apache

```
systemctl enable httpd
```

## mysql

1.[centos7](https://so.csdn.net/so/search?q=centos7&spm=1001.2101.3001.7020)中安装wget

```
yum -y install wget
```

2.下载MySQL源

```
wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm 
```

3.安装 mysql-community-release-el7-5.noarch.rpm 包

```
rpm -ivh mysql-community-release-el7-5.noarch.rpm
```

4.查看是否安装成功

```
ls -1 /etc/yum.repos.d/mysql-community*
```

5.使用yum安装mysql

```
yum install mysql-server -y
```

6.启动mysql

```
systemctl restart mysql
```

7.设置 MySQL 账户名和密码

```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '您的数据库密码' WITH GRANT OPTION;
flush privileges;
```

如果未生效，可以直接使用`SET PASSWORD = PASSWORD('12345678');`

8.将 MySQL 设置为开机自动启动：

```
systemct enable mysqld
```

## PHP

1.配置PHP7的源

```
yum install epel-release
```

2.增加PHP7的源

```
rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
```

3.安装php7-fpm

```
yum install php70w-fpm php70w-cli php70w-gd php70w-mcrypt php70w-mysql php70w-pear php70w-xml php70w-mbstring php70w-pdo php70w-json php70w-pecl-apcu php70w-pecl-apcu-devel
```

4.启动

```
systemctl start php-fpm
```

## PHP+Nginx配置

1.nginx的配置目录/etc/nginx/nginx.conf

```
server {
    listen 80;
    server_name (站点域名 没有就用IP代替);
    root  /usr/share/nginx/html(网站根目录);
    index index.php index.html;
    location ~ \.php$ {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_index  index.php;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include        fastcgi_params;
    }
}
```

2.站点目录下面创建index.php

```
<?php
 	phpinfo(); 
 ?>
```

3.配置php-fpm 位置在/etc/php-fpm.d/www.conf

```
user = apache
group = apache
#将原来的apache改成nginx ，站点的目录拥有者给nginx
user = nginx
group = nginx
```

4.配置完重启nginx与php-fpm