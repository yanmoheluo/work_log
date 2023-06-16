**【QQ登录】接入规范** ^5f75da

**[准备工作_OAuth2.0 — QQ互联WIKI](https://wiki.connect.qq.com/%e5%87%86%e5%a4%87%e5%b7%a5%e4%bd%9c_oauth2-0)**
# 成为开发者

**开发者通过以下几个步骤，即可接入互联开放平台： 注册开发者→创建应用→通过审核并获取接口权限**

## 1.注册开发者

1. 在QQ互联开放平台首页 [https://connect.qq.com/](https://connect.qq.com/) ，点击右上角的“登录”按钮，使用QQ帐号登录，如下图所示：  
![](https://wiki.connect.qq.com/wp-content/uploads/2017/02/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20180725150349.png)

**重要提示：**  
开发者QQ号码一旦注册不能变更，建议使用公司公共QQ号码而不是员工私人号码注册，以免遇到员工离职等情况造成不必要的麻烦。

![](https://wiki.connect.qq.com/wp-content/uploads/2017/02/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20180801170555.png)  
2. 登录成功后会跳转到开发者注册页面，在注册页面按要求提交公司或个人的基本资料。下图所示的是公司注册页面：  
![](https://wiki.connect.qq.com/wp-content/uploads/2017/02/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20180801170447.png)  
3.按要求提交资料后，审核人员会进行审核，通过审核即可成为开发者。
# 创建应用

## 网站应用及移动应用接入申请

   
应用接入前，首先需进行申请，获得对应的appid与appkey，以保证后续流程中可正确对网站与用户进行验证与授权。

### 1.1 创建应用

开发者注册完成后，点击“应用管理”按钮。  
![](https://wiki.connect.qq.com/wp-content/uploads/2016/12/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20180801172542.png)  
跳转到qq互联管理中心页面，点击创建应用。  
![](https://wiki.connect.qq.com/wp-content/uploads/2016/12/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20180801172748.png)  
选择需要创建的应用类型，我们以网站应用为例：  
![](https://wiki.connect.qq.com/wp-content/uploads/2016/12/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20180801172919.png)  
点击创建网站应用后，按要求完善信息：  
![](https://wiki.connect.qq.com/wp-content/uploads/2016/12/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20180801173039.png)  
![](https://wiki.connect.qq.com/wp-content/uploads/2016/12/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20180802162344_%E7%9C%8B%E5%9B%BE%E7%8E%8B.png)

1. 网站回调地址填写规范：[https://wiki.connect.qq.com/%E5%9B%9E%E8%B0%83%E5%9C%B0%E5%9D%80%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98%E5%8F%8A%E4%BF%AE%E6%94%B9%E6%96%B9%E6%B3%95](https://wiki.connect.qq.com/%E5%9B%9E%E8%B0%83%E5%9C%B0%E5%9D%80%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98%E5%8F%8A%E4%BF%AE%E6%94%B9%E6%96%B9%E6%B3%95)
2. 备案信息填写规范：[http://www.miitbeian.gov.cn/publish/query/indexFirst.action](http://www.miitbeian.gov.cn/publish/query/indexFirst.action)

![](https://wiki.connect.qq.com/wp-content/uploads/2016/12/TIM%E5%9B%BE%E7%89%8720180802162713.png)  
网站信息填写完成，点击“创建应用”后，网站应用创建完成，点击“应用管理”，进入管理中心，在管理中心可以查看到网站获取的appid和appkey，如下图所示：  
![](https://wiki.connect.qq.com/wp-content/uploads/2016/12/TIM%E5%9B%BE%E7%89%8720180802162906.png)  
备注：创建移动应用与网站应用步骤方法一致，在此不赘述。  
 

### 1.2 网站信息完善

点击“应用中心”，应用右侧的“查看”，进入应用详情页面。  
![](https://wiki.connect.qq.com/wp-content/uploads/2016/12/TIM%E5%9B%BE%E7%89%8720180802163026.png)  
应用详情页面可点击“修改”来编辑应用“基本信息”和“平台信息”。  
![](https://wiki.connect.qq.com/wp-content/uploads/2016/12/TIM%E5%9B%BE%E7%89%8720180802163233.png)  
![](https://wiki.connect.qq.com/wp-content/uploads/2016/12/TIM%E5%9B%BE%E7%89%8720180802163335.png)  
点击“应用接口”可查看已获取的接口，使用QQ登录功能。  
![](https://wiki.connect.qq.com/wp-content/uploads/2016/12/TIM%E5%9B%BE%E7%89%8720180802163428.png)

# 公共返回码说明

## 公共返回码-for OAuth2.0协议

### 100000-100031：PC网站接入时的公共返回码

|错误码|含义说明|
|---|---|
|0|成功。|
|100000|缺少参数response_type或response_type非法。|
|100001|缺少参数client_id。|
|100002|缺少参数client_secret。|
|100003|http head中缺少Authorization。|
|100004|缺少参数grant_type或grant_type非法。|
|100005|缺少参数code。|
|100006|缺少refresh token。|
|100007|缺少access token。|
|100008|该appid不存在。|
|100009|client_secret（即appkey）非法。|
|100010|回调地址不合法，常见原因请见：[回调地址常见问题及修改方法](https://wiki.connect.qq.com/%e5%9b%9e%e8%b0%83%e5%9c%b0%e5%9d%80%e5%b8%b8%e8%a7%81%e9%97%ae%e9%a2%98%e5%8f%8a%e4%bf%ae%e6%94%b9%e6%96%b9%e6%b3%95 "回调地址常见问题及修改方法")|
|100011|APP不处于上线状态。|
|100012|HTTP请求非post方式。|
|100013|access token失效（用户取消授权或过期被回收）。|
|100014|access token过期。 token过期时间为30天。如果存储的access token过期，请重新走登录流程，根据[使用Authorization_Code获取Access_Token](https://wiki.connect.qq.com/%e4%bd%bf%e7%94%a8authorization_code%e8%8e%b7%e5%8f%96access_token "使用Authorization_Code获取Access_Token")或[使用Implicit_Grant方式获取Access_Token](https://wiki.connect.qq.com/%e4%bd%bf%e7%94%a8implicit_grant%e6%96%b9%e5%bc%8f%e8%8e%b7%e5%8f%96access_token "使用Implicit_Grant方式获取Access_Token")获取新的access token值。|
|100015|access token废除。 token被回收，或者被用户删除。请重新走登录流程，根据[使用Authorization_Code获取Access_Token](https://wiki.connect.qq.com/%e4%bd%bf%e7%94%a8authorization_code%e8%8e%b7%e5%8f%96access_token "使用Authorization_Code获取Access_Token")或[使用Implicit_Grant方式获取Access_Token](https://wiki.connect.qq.com/%e4%bd%bf%e7%94%a8implicit_grant%e6%96%b9%e5%bc%8f%e8%8e%b7%e5%8f%96access_token "使用Implicit_Grant方式获取Access_Token")获取新的access token值。|
|100016|access token验证失败。|
|100017|获取appid失败。|
|100018|获取code值失败。|
|100019|用code换取access token值失败。|
|100020|code被重复使用。code是一次性有效的，开发者此时应该引导用户重新登录授权，重新获取code，而不是重试token接口|
|100021|获取access token值失败。注：refresh_token仅一次有效，每次续票成功，都会返回最新的refrush_token|
|100022|获取refresh token值失败。|
|100023|获取app具有的权限列表失败。|
|100024|获取某OpenID对某appid的权限列表失败。|
|100025|获取全量api信息、全量分组信息。|
|100026|设置用户对某app授权api列表失败。|
|100027|设置用户对某app授权时间失败。|
|100028|缺少参数which。|
|100029|错误的http请求。|
|100030|用户没有对该api进行授权，或用户在腾讯侧删除了该api的权限。请用户重新走登录、授权流程，对该api进行授权。|
|100031|第三方应用没有对该api操作的权限。请发送邮件进行[OpenAPI权限申请](https://wiki.connect.qq.com/openapi%e6%9d%83%e9%99%90%e7%94%b3%e8%af%b7 "OpenAPI权限申请")。|
|100032|过载，一开始未细分时可以用。|
|100033|缺少UIN参数。|
|100034|缺少skey参数。|
|100035|用户未登陆。|
|100036|RefreshToken失效。|
|100037|RefreshToken已过期|
|100038|RefreshToken已废除|
|100039|RefreshToken到达调用上限。|
|100040|RefreshToken的AppKey非法。|
|100041|RefreshToken,AppID非法。|
|100042|RefreshToken非法。|
|100043|APP处于暂停状态。|
|100044|错误的sign，Md5校验失败，请求签名与官网填写的签名不一致。|
|100045|用户改密token失效。|
|100046|g_tk校验失败。|
|100048|没有设置companyID。|
|100049|APPID没有权限(get_unionid)。|
|100050|OPENID解密失败，一般是openid和appid不匹配。|
|100051|调试模式无权限。|
|100052|APPID没有权限获取paytoken和openid|
|100053|ip没有权限获取用户登录信息|
|100054|查询用户近期登录记录时缺少uin参数|
|100055|查询用户授权信息失败|
|100056|该用户近期没有授权记录|
|100057|APPID没有使用skey换code或token的权限|
|100058|openid非法|
|100059|ip没有权限使用接口|
|100060|禁止登录|
|100061|非法apptoken|
|100062|应用频率限制|
|100063|获取openid失败|
|100065|获取delegatetoken失败|
|100066|没有权限获取delegatetoken|
|100067|code过期|
|100068|非法code|
|110401|请求的应用不存在。|
|110404|请求参数缺少appid。|
|110405|登录请求被限制，请稍后在登录。|
|110406|应用没有通过审核。|
|110500|获取用户授权信息失败。|
|110501|获取应用的授权信息失败|
|110502|设置用户授权失败|
|110503|获取token失败|
|110504|系统内部错误|
|110505|参数错误|
|110506|获取APP info信息失败|
|110507|校验APP info 签名信息失败|
|110508|获取code失败|
|110509|SKEY校验失败|
|110510|Disable|

##   
公共返回码-for 网站验证失败

|错误码|含义说明|
|---|---|
|100001|网站url格式不正确（网站url长度不能超过256，网站url只能有二级目录）|
|100003|服务器连接超时。|
|103001|网站的mete信息和QQ提供的验证信息不一致。|
|103002|网站不能使用IP地址和端口号。|