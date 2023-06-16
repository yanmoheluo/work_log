安装httpd

```bash
yum install -y httpd httpd-devel httpd-server mod_ssl openssl
```

安装mariadb

```bash
yum install -y mariadb mariadb-server mariadb-libs mariadb-devel 
```

启动

```bash
service mariadb start 
```

设置密码

```bash
mysql_secure_installation
#输入密码-确认密码-y-y-y-y
```

修改配置文件添加并重启mysql：

```bash
[mysqld]
skip-name-resolve
#skip-name-resolve 参数的目的是不再进行反解析（ip不反解成域名），这样可以加快数据库的反应时间。
```

切换[centos7](https://so.csdn.net/so/search?q=centos7&spm=1001.2101.3001.7020) php7源

```bash
rpm -Uvh https://mirror.webtatic.com/yum/el7/epel-release.rpm
rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
```

安装php

```bash
yum install -y mod_php71w php71w-cli php71w-common php71w-devel php71w-fpm php71w-gd php71w-mbstring php71w-mysql php71w-odbc php71w-pdo php71w-xml php71w-xmlrpc php71w-process
```

设置开机自启动

```bash
systemctl enable httpd
systemctl enable mariadb
```