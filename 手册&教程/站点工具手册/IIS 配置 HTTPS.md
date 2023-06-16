###   **前言**

　　HTTPS（全称：Hyper Text Transfer Protocol over Secure Socket Layer 或 Hypertext Transfer Protocol Secure，超文本传输安全协议），是以安全为目标的HTTP通道，简单讲是HTTP的安全版。使用SSL证书，实现网站HTTPS化，使网站可信，防劫持、防篡改、防监听。

###   **证书申请和准备**

　　在国内，我们可以通过多种渠道申请 HTTPS 证书，有收费版和免费版。一般情况下天下没有免费的午餐，免费版谁知道有多少坑等着你呢？国内几乎所有的云产生都提供 HTTPS 证书申请业务，比如：阿里云，腾讯云，华为云，百度云等等。

　　我有阿里云ECS服务器，目前申请赛门铁克证书是免费的。

　　赛门铁克是 SSL/TLS 证书的领先提供商，为全球一百多万台网络服务器提供安全防护。我这里从阿里云申请了一个赛门铁克的 HTTPS 证书，下载下来是一个压缩文件。

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps26.jpg) 

　　从图上可以看到，压缩文件中一共有两个文件。证书文件和密码文件。在此我们的 HTTPS证书就准备完毕。

###   **在服务器上安装HTTPS证书**

　　本机采用 Windows Server 2012 + IIS 8.0 环境。

　　1. 开始 -> 运行 -> MMC ；  
 ![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps27.jpg)

 　　2. 打开 MMC；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps28.jpg) 

　　3. 文件 -> 添加/删除管理单元；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps29.jpg) 

　　4. 双击 证书 或 选中证书 ，点击添加；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps30.jpg) 

 　　5. 选择 计算机账户 -> 下一步；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps31.jpg) 

 　　6. 选择 本地计算机(运行次控制台的计算机) -> 完成；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps32.jpg) 

　　7. 确定；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps33.jpg) 

　　8. 控制台根节点 -> 证书 -> 个人 -> 证书 -> 右键 -> 所有任务 -> 导入；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps34.jpg) 

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps35.jpg) 

　　9. 下一步；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps36.jpg) 

　　10. 从 我们准备的 证书文件中 选择证书（我们申请的是*.pfx 文件），选好之后，单击下一步；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps37.jpg) 

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps38.jpg) 

　　11. 输入证书密码（密码来源于：pfx-password.txt 文件），输入完毕后 单击 下一步；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps39.jpg) 

　　12. 从图上可以看到，我们新添加证书已经成功；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps40.jpg) 

###   **在IIS上配置证书**

　　证书安装完毕之后，需要在IIS上配置网站的证书。 

　　1. 打开 IIS， 在我们需要配置的网站上面右键，编辑绑定；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps41.jpg) 

　　2. 添加 HTTPS 绑定；

　　　　类型选择为 https

　　　　端口 443

　　　　ip地址选择本机外网ip

　　　　主机名设置为 域名

　　　　勾选 需要服务器名称指示

　　　　SSL证书请选择 刚刚我们配置的证书 （如不清楚该选择哪个证书，可以选择一个证书之后点击查看，从查看中可以辨别该证书是否为我们需要的证书）

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps42.jpg) 

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps43.jpg) 

　　3. 添加 HTTPS 绑定完毕后，我们可以看到 绑定列表中已经存在端口为 443 的绑定（HTTPS 已经配置好啦）；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps44.jpg) 

　　4. HTTPS 已经配置好啦，接下来 打开 浏览器验证一下（可以看到 输入 https://ap123.test.com 已经可以使用）；

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps45.jpg)