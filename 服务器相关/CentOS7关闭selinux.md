## 1、为什么要关闭selinux

安装[apache](https://so.csdn.net/so/search?q=apache&spm=1001.2101.3001.7020)服务器部署PHP后端时会出现赋权失败的问题，总结了一下原因是因为开启了SELinux导致，初学者配置linux服务器时不成功，却没有头绪，那是因为在linux操作系统中默认开启了防火墙，SELinux也处于启动状态，一般状态为enforing。致使很多服务端口默认是关闭的。所以好多服务初学者明明配置文件正确，等验证时有时连ping也ping不通。建议初学者在未学到SELlinux与iptables之前，配置服务器把这两项都关掉。

## 2、查看selinux状态

```
getenforce
```

enforcing为开启、disable为关闭

## 3、临时关闭selinux

如果你只是想临时关闭selinux用下面这个就好了（重启后会恢复开启状态）

```
setenforce 0
```

## 4、永久关闭selinux

如果你想永久关闭打开下面这个文件

```
vi /etc/selinux/config
```

将：SELINUX=enforcing改为SELINUX=disabled  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200326221543303.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTc4Njg2MQ==,size_16,color_FFFFFF,t_70)  
用命令reboot重启生效