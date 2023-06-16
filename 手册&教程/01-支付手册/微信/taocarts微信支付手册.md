微信公众号申请教程:https://jingyan.baidu.com/article/e8cdb32b0bb7de37042bad7b.html

微信商户平台申请:https://jingyan.baidu.com/article/e8cdb32b0bb7de37042bad7b.html

首先申请微信公众号服务号和商户号，这个就不说了，下面介绍插件用于支付需要的信息。

 * TODO: 修改这里配置为您自己申请的商户信息

 * 微信公众号信息配置

 *

 * APPID：绑定支付的APPID（必须配置，开户邮件中可查看）

 *

 * MCHID：商户号（必须配置，开户邮件中可查看）

 *

 * KEY：商户支付密钥，参考开户邮件设置（必须配置，登录商户平台自行设置）

 * 设置地址：https://pay.weixin.qq.com/index.php/account/api_cert

 *

 * APPSECRET：公众帐号secert（仅JSAPI支付的时候需要配置， 登录公众平台，进入开发者中心可设置），

 * 获取地址：[https://mp.weixin.qq.com/advanced/advanced?action=dev&t=advanced/dev&token=2005451881&lang=zh_CN](https://mp.weixin.qq.com/advanced/advanced?action=dev&t=advanced/dev&token=2005451881&lang=zh_CN)

微信支付配置流程：

**微信支付配置，必须满足以下条件：**

1、拥有公众帐号，且为服务号；  
2、公众帐号须通过微信认证；（未认证用户，可先申请微信认证）  
3、微信支付接口已经开通

**1、打开开发配置**

登录[微信支付商户平台](https://pay.weixin.qq.com/)（[https://pay.weixin.qq.com/](https://pay.weixin.qq.com/))，选择“产品中心”，点击“开发配置”

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps4.jpg) 

**2、编辑微信支付设置**

1）选择支付授权目录（JSAPI授权目录）  
2）支付授权目录添加以下两个链接：ana.soperson.com/wemall/pay/wpay/，www.leyu99.net/wemall/pay/wpay/

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps5.jpg) 

**3、网页授权获取用户基本信息配置**

1）登录[公众平台](http://mp.weixin.qq.com/)（[mp.weixin.qq.com](http://mp.weixin.qq.com/))，选择右上角“公众号设置”， 点击“功能设置”，选择“网页授权域名”，点击修改  
2）授权回调页面域名填写：ana.soperson.com/wemall/， 保存

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps6.jpg) 

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps7.jpg) 

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps8.jpg)