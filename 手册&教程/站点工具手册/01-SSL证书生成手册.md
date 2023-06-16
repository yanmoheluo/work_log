**商户证书生成手册**

**V1.0.0**

# 1. **操作流程**

## 1.1 **商户证书生成**

**前提**：

ü 已开通商户管理平台账户。

ü 具有商户证书管理权限。

**功能：**

“10012256484.pfx “证书用于send页面对提交的参数组成串后的签名，主要作用是防止商户提交的数据传输过程中被篡改。” public-rsa.cer“证书用于receive页面中对系统返回的参数进行验签，主要作用是验证系统返回给商户的参数没有被篡改。

**操作流程：**

1. 证书生成软件安装

附件OpenSSL 文件夹直接复制到本地即可使用，openssl.exe程序用于生成证书。

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps14.png)

2. 证书生成

2.1. 如下图，打开OpenSSL/bin/openssL.exe

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps15.jpg) 

2.2. 输入genrsa -out private-rsa.key 1024，按enter即可。

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps16.png) 

2.3. 输入req -new -x509 -key private-rsa.key -days 750 -out public-rsa.cer，按enter，然后按照第二个图片提示进行填写。

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps17.png) 

注：如报错，则根据工具所在路径指定下配置文件，如命令改为：req -new -x509 -key private-rsa.key -config "D: \OpenSSL\bin\openssl.cnf" -days 750 -out public-rsa.cer

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps18.png) 

2.4. 输入pkcs12 -export -name test-alias -in public-rsa.cer -inkey private-rsa.key -out dc-rsa.pfx，按enter，然后按照第二个图输入密码，密码输入时不会显示出来。商户必须记住该密码，在代码中需要用到。此命令中test-alias为证书别名，在交易时需要使用。

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps19.jpg) 

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps20.png) 

2.5. 如下，进入openssl的bin目录，可以看到执行以上命令后生成的两个证书。

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps21.jpg) 

2.6.登陆商户管理平台：https://global.chinapnr.com/site/index.htm，进入Platform Management菜单下Certificate Management菜单。使用开通时的账户密码登录，在证书管理，输入邮箱，点击Do Upload上传证书。并点击Download下载系统公钥用于接收跨境系统返回时验签。

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps22.jpg) 

2.7. 如果是使用PHP的商户，需要将“dc-rsa.pfx”证书转换为“dc-rsa.pem”，输入转换命令pkcs12 -in dc-rsa.pfx -passin pass:此处输入商户第4步设置的密码 -nodes -out dc-rsa.pem，按enter即可。进入openssl的bin目录，此时可以看到pem格式证书已经生成。

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps23.jpg) 

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps24.jpg) 

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps25.jpg) 

转化私钥。