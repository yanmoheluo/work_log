**https://cloud.tencent.com/developer/article/1620409**

**Facebook应用配置**

1. 在 [https://developers.facebook.com](https://developers.facebook.com/) 开通Facebook开发者账号

2. 创建应用

3. 配置相关参数，在这里把AppId(应用编号)和AppSecret(应用秘钥)记下来。

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps148.png)

1. 添加产品

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps149.png)

可以添加Android、IOS、web页面等类型的授权登录

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps150.png)

**前端授权**

1. 配置回调地址。这里以网页版的授权为例，如果开发网页版的Facebook授权登录，需要在Facebook后台配置**有效OAuth跳转URI**，就是用户在Facebook登录页面登录成功之后需要回调到**部署你自己的登录页面的服务器地址**。

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps151.png)

1. 授权登录sdk，Facebook官方提供了详细的说明，也有现成的sdk和完整的demo。官方文档： [https://developers.facebook.com/docs/facebook-login/web](https://developers.facebook.com/docs/facebook-login/web) 示例：login.html

<html>

    <head>

        <script async defer crossorigin="anonymous" src="https://connect.facebook.net/en_US/sdk.js#xfbml=1&version=v6.0&appId=746492673568696&autoLogAppEvents=1"></script>

        <script>

            function login() {

                FB.login(function(response){

                    console.log(response);

                });

            }

        </script>

    </head>

    <body>

        <h1>Facebook登录</h1>

        <!-- 自定义登录按钮 -->

        <button id="loginBtn" onclick="login();" >登录</button> 

    </body>

</html>

           这个网页不能直接用浏览器打开，需要部署在支持https的服务器上。

           下面是登录过程的截图

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps152.png)

           登录成功之后可以看到控制台打印出了登录成功后Facebook返回的信息，有accessToken、userID等：

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps153.png)

**后端校验**

       前端拿到登录token后，需要后端校验一下，防止别人拿其他平台的appId授权的token来请求。

       可以用 https://graph.facebook.com/debug_token?access_token={App-token}&input_token={User-token}这个接口来校验token，User-token为用户登录的token（比如上面用户登录返回的accessToken），App-token是由appId和appSecret拼接而成，格式为 {appId}%7C{appSecret}，%7C就是|urlencode之后的编码。

       比如appId是746492673568696，appSecret是71cf85a8ba36c84b22bc3461e143e16b，那就可以直接用发送get请求https://graph.facebook.com/debug_token?access_token=746492673568696%7C71cf85a8ba36c84b22bc3461e143e16b&input_token=前端用户登录返回的accessToken，返回结果的格式如下

{

    "data": {

        "app_id": "746492673568696",

        "type": "USER",

        "application": "shop",

        "data_access_expires_at": 1594896505,

        "expires_at": 1587124800,

        "is_valid": true,

        "scopes": [

            "user_birthday",

            "user_likes",

            "user_photos",

            "user_friends",

            "user_status",

            "email",

            "public_profile"

        ],

        "user_id": "110029804771531"

    }

}

       其中is_valid就是token是否校验成功。如果还需要获取其他用户信息，可以参考Facebook提供的api [https://developers.facebook.com/docs/graph-api/using-graph-api](https://developers.facebook.com/docs/graph-api/using-graph-api)

本文参与[腾讯云自媒体分享计划](https://cloud.tencent.com/developer/support-plan)，欢迎正在阅读的你也加入，一起分享。