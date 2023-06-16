测试时遇到将一本地目录设置为一apache的虚拟主机，在httpd-vhosts.conf文件中进行简单设置，然后在hosts文件中将访问地址指向本地，启动apache，进行访问，却出现了You don’t have permission to access / on this server的提示，baidu了一下，原来是因为我的虚拟主机目录为非apache安装目录下的htdocs，所以违反了apache对默认对网站根访问权限。

apache的默认虚拟主机根目录地址为…/Apache Software Foundation/Apache2.2/htdocs 目录下，需要对httpd.conf文件进行修改才能指向其他目录。

在httpd.conf文件下找到这段：

```
DocumentRoot "C:/Program Files/Apache24/htdocs"
```

上面这个地址是你服务器的根目录  
接下来为你的根目录配置访问权限

```
<Directory "C:/Program Files/Apache24/htdocs">
   Options Indexes FollowSymLinks
   AllowOverride None
   Require all granted
</Directory>
```

然后重启apache，就ok了。

如果要配置自己的根目录，则将DocumentRoot中的地址换为你自己的地址，并为给该目录相应权限。


