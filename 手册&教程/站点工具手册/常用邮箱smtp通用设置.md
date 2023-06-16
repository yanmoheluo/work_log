发送邮件的时候smtp错误：登录失败

Linux主机的客户，可以使用服务器自带的邮箱

邮箱设置，勾选ssl的，需要服务器环境支持openssl，开启ssl的方法：

**一、将php安装目录下的这3个文件复制到%system%/system32目录下：php_openssl.dll、libeay32.dll、ssleay32.dll**

**二、****打开php.ini****(****在****phpinfo****里查看它的位置****)，将“;extension=php_openssl.dll****”前面分号去掉。**

**三、****重启IIS****或****apache**

163企业邮箱的设置

Auth 验证

Ssl  验证

端口 994

163邮箱：

smtp地址：smtp.163.com

Auth认证： 验证

SSL：  不验证

端口： 25

状态：启用

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps84.jpg)

Qq邮箱：http://service.mail.qq.com/cgi-bin/help?subtype=1&&id=28&&no=334#1

Smtp: smtp.qq.com

两个验证都需要

端口：465

Qq企业邮箱：

Smtp: smtp.exmail.qq.com

两个验证都需要

端口：465

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps85.jpg)

Gmail 邮箱

Smtp: smtp.gmail.com

Auth 验证

Ssl 验证

端口：465

Gmail邮箱，如果服务器和注册gmail时的ip不在同一个ip段，就会显示smtp错误：登录失败。拒绝登录。

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps86.jpg)

服务器提供的邮箱 ：

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps87.jpg)

阿里云邮箱：

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps88.jpg) 

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps89.jpg) 

Yandex邮箱：

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps90.jpg)