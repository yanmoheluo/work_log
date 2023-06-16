1、首先安装 zend guard 5.5

注册 key

： zend_guard.zl

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps122.jpg)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps123.png) 

**22、新建 zend guard project**

**2.1 编辑项目信息（project Infomation）**

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps124.jpg)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps125.png) 

**2.2 选择需要加密的源文件路径**

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps126.jpg)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps127.png) 

2.3 设置加密的文件类型

经测试 只可以加密 php 文件，不可以加密 tpl 文件，加密 tpl 会报 Arrary 错误。![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps128.jpg)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps129.png)

3、设置文件头信息

点击右侧的头信息（Header Information）

选择不显示头（Don't display any header）![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps130.jpg)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps131.png)

4、生成 KEY

点击安全（Security）

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps132.jpg)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps133.png) 

右上角【Expiration】设置有效期时间 默认永不过期

4.1 选择使用 license（Enable License SupPort）

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps134.jpg)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps135.png) 

4.2 生成加密 key

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps136.jpg)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps137.png) 

     选择 licensekey 下面的 Generated

     点击 configure lincense Keys

     删除原来，重新生成一个 key

    【请确认是否生成成功】

4.3 生成加密文件

点击 Generate Product LicenseFile

选择产品名称

输入授权给。。。

保存授权文件

【下一步】

设置 IP 限制 mac 地址限制

【请确认是否生成成功】

5、开始加密

在工程文件上面右键选择【encoding project】

【请确认是否生成成功】

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps138.jpg)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps139.png) 

66、加密完成替换工程文件

htdocs 和授权文件拷贝到

apache 根目录下即可

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps140.jpg)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps141.png)