### CentOS7开启SSH服务

  
在虚拟机（Vmware Workstation）下，安装了CentOS7，现在想通过SSH工具连接虚拟机中的CentOS7

1、 首先，要确保CentOS7安装了 [openssh](https://so.csdn.net/so/search?q=openssh&spm=1001.2101.3001.7020)-server，在终端中输入 yum list installed | grep openssh-server  
![在这里插入图片描述](https://img-blog.csdnimg.cn/e9e81565036849428211fc7fd2e1d611.png)

此处显示已经安装了 openssh-server，如果又没任何输出显示表示没有安装 openssh-server，通过输入 yum install openssh-server

![在这里插入图片描述](https://img-blog.csdnimg.cn/ce913a94d5d44cff967cc435d3178b7b.png)

来进行安装openssh-server

2、 找到了 /etc/ssh/ 目录下的[sshd](https://so.csdn.net/so/search?q=sshd&spm=1001.2101.3001.7020)服务配置文件 sshd_config，用Vim编辑器打开

将文件中，关于监听端口、监听地址前的 # 号去除

![在这里插入图片描述](https://img-blog.csdnimg.cn/14141a4d60e643a4ae90f9011c0ee99a.png)

然后开启允许远程登录

![在这里插入图片描述](https://img-blog.csdnimg.cn/f1fd8ae67eaa492ab8046271771116ad.png)

最后，开启使用用户名密码来作为连接验证

![在这里插入图片描述](https://img-blog.csdnimg.cn/2ac783c060584677bfd1086672cc1c3d.png)

保存文件，退出

3、 开启 sshd 服务，输入 sudo service sshd start

![在这里插入图片描述](https://img-blog.csdnimg.cn/8bce994b56b842b2935c9c35fb97ae39.png)

检查 sshd 服务是否已经开启，输入ps -e | grep sshd

![在这里插入图片描述](https://img-blog.csdnimg.cn/3a6c30a935274990bef08199a55c6659.png)

或者输入netstat -an | grep 22 检查 22 号端口是否开启监听

![在这里插入图片描述](https://img-blog.csdnimg.cn/d3bc344916624de4ba1d66e60245ee8f.png)

4、 在Vmware Workstation中，查看CentOS7的属性，发现网络连接方式是采用的 NAT 方式连接的

![在这里插入图片描述](https://img-blog.csdnimg.cn/0c771318f86e48369ef5eb1c0ec7829c.png)

5、 在Vmware Workstation中，点击编辑=》虚拟网络编辑器，进入虚拟网络编辑器，查看发现 NAT 模式的连接采用的网络适配器名称为VMnet8

![在这里插入图片描述](https://img-blog.csdnimg.cn/d386463614f645578c697ca3580fafc7.png)

6、在 windows 主机中，在命令行中输入ipconfig 查看主机IP，找到 VMnet8 的连接信息，此处 ip 为192.168.30.1

![在这里插入图片描述](https://img-blog.csdnimg.cn/f09e02eb2c4c49439ff38e17e33d6620.png)

7、在CentOS中，输入ifconfig查看网络连接地址，发现CentOS的网络地址为192.168.112.128

![在这里插入图片描述](https://img-blog.csdnimg.cn/c6420698eacb4f948c7a632d1d57e348.png)

8、在CentOS中，输入ping 192.168.30.1 测试是否能连通主机，发现可以连通

![在这里插入图片描述](https://img-blog.csdnimg.cn/04bf6789103442288d9ee239cb23be4b.png)

9、在主机中，输入 ping 192.168.112.128，测试主机是否能连通CentOS，发现连不通，如果可以连得通，可以直接跳至第12 步

10、在主机，打开网络配置，选择网络适配器 VMnet8 的 TCP/IPv4 的属性，进行一下网络配置要求子网掩码、默认网关均和CentOS一致，并将IP地址修改为 192.168.112.1，即保证主机的 IP 和 CentOS 的 IP 在同一网络区段中

11、再在主机中，输入 ping 192.168.112.128，已经可以连接得通了

12、在SSH工具（此处使用的XShell）中，新建连接，输入 CentOS 的 IP 地址、用户名、密码即可连接成功

连接成功

13、为了免去每次开启 CentOS 时，都要手动开启 sshd 服务，可以将 sshd 服务添加至自启动列表中，输入systemctl enable sshd.service

![在这里插入图片描述](https://img-blog.csdnimg.cn/7a3182dfa51f44c0a66620b9f4b0a93c.png)

可以通过输入systemctl list-unit-files | grep sshd，查看是否开启了sshd 服务自启动

![在这里插入图片描述](https://img-blog.csdnimg.cn/0412a9873076415e93455e724517581c.png)

以上内容原文地址：https://blog.csdn.net/qq_36663951/article/details/79813038