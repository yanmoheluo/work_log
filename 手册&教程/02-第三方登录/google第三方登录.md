**第三方Google登录**

**https://juejin.cn/post/6844903746426798088**

1、获取客户端ID（https://console.developers.google.com/apis/credentials），如下图：

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps154.png)

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps155.png)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps156.png)https://user-gold-cdn.xitu.io/2018/12/24/167dfac5acdaf21b?imageView2/0/w/1280/h/960/format/webp/ignore-error/1

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps157.png) [https://user-gold-cdn.xitu.io/2018/12/24/167dfaa722d164ef?imageView2/0/w/1280/h/960/format/webp/ignore-error/1](https://user-gold-cdn.xitu.io/2018/12/24/167dfaa722d164ef?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

https://user-gold-cdn.xitu.io/2018/12/24/167dfad9f0cdca21?imageView2/0/w/1280/h/960/format/webp/ignore-error/1

2、加载Google API平台库以创建gapi对象(https://apis.google.com/js/platform.js)：

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps158.png)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps159.png)![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps160.png)https://user-gold-cdn.xitu.io/2018/12/24/167dfad9f0cdca21?imageView2/0/w/1280/h/960/format/webp/ignore-error/1

ps:这里面要注意，使用Google API的之前要在谷歌后台启用people API库,如图：https://user-gold-cdn.xitu.io/2018/12/24/167dfb5f8cb5cb66?imageView2/0/w/1280/h/960/format/webp/ignore-error/1

![](file:///C:\Users\zzqss\AppData\Local\Temp\ksohtml8680\wps161.png)https://user-gold-cdn.xitu.io/2018/12/24/167dfb715fd16aa9?imageView2/0/w/1280/h/960/format/webp/ignore-error/1

点击启用即可。

3、上述配置完成后，就可以开始接sdk了，首先加载auth2库：

**function** onInitGoogle (opts, sccess, error) {

  // let getAuthInstance = {};

  let baseOptions = {

    client_id: '你的客户端ID',

    cookiepolicy: 'single_host_origin'

  };

  let options = {...baseOptions, ...opts};

  gapi.load ('auth2', **function** () {

    gapi.auth2.init (options).then (res => {

      sccess (res);

    }, err => {

      error (err);

    });

  });

}复制代码

一、gapi.load()方法：是加载auth2的库，左右方法要在此方法加载完成后才可以用。

二、gapi.auth2.init()方法：初始化GoogleAuth对象，该方法是为后面的             gapi.auth2.getAuthInstance方法的初始化。

4、初始化操作之后调用gapi.auth2.getAuthInstance方法，这个方法可以让你获取用户的基本信息，当前的登录状态及注销等基本操作

**function** **getAuthInstance** () {

  return gapi.auth2.getAuthInstance ();

}复制代码

5、Google登录

/**

 *google登录

 */

**function** googleSignIn (success, error) {

  this.getAuthInstance.signIn ().then (**function** (res) {

    success (res);

  }, **function** (err) {

    error (err);

  });

}复制代码

一、这里面的this.getAuthInstance方法就是步骤4定义的方法;

二、这里面的then是google自己封装的promise,直接then就可以获取返回的结果。有两个参数，onInit和onError;

最后附上一个完成的调用方法示例,详细的方法参考(https://developers.google.com/identity/sign-in/web/reference#gapiauth2authresponse)：

//ThirdPartyLogin.js

/**

 * 初始化谷歌登录

 * @param opts

 * @param sccess

 * @param error

 */

**function** onInitGoogle (opts, sccess, error) {

  // let getAuthInstance = {};

  let baseOptions = {

    client_id: '你的客户端ID',

    cookiepolicy: 'single_host_origin'

  };

  let options = {...baseOptions, ...opts};

  gapi.load ('auth2', **function** () {

    gapi.auth2.init (options).then (res => {

      sccess (res);

    }, err => {

      error (err);

    });

  });

}

/**

 * 初始化谷歌的getAuthInstance

 * GoogleAuth 是一个单例类，提供允许用户使用Google帐户登录，获取用户当前登录状态，从用户的Google个人资料中获取特定数据，请求其他范围以及从当前帐户注销的方法。

 * @returns {*}

 */

**function** **getAuthInstance** () {

  return gapi.auth2.getAuthInstance ();

}

/**

 *google登录

 */

**function** googleSignIn (success, error) {

  this.getAuthInstance.signIn ().then (**function** (res) {

    success (res);

  }, **function** (err) {

    error (err);

  });

}

const ThirdPartyLogin = {

  onInitGoogle,

  getAuthInstance,

  googleSignIn

};

export default ThirdPartyLogin;

复制代码

//index.js

import ThirdPartyLogin from './ThirdPartyLogin';

class Platform {

  **constructor** () {

    this.onInit ();

  }

  **onInit** () {

    this.onInitEvent ();

    this.onInitDomEvent ();

    this.onInitGoogleEvent ();//初始化谷歌事件

}

  **onInitEvent** () {//订阅google登录事件

    $.subscribe ('onGoogleLoginEvent', this.onGoogleLoginEvent.bind (this));

  }

  **onInitDomEvent** () {//点击google登录发布事件

    $ ('#gl-login-button').click (**function** () {

      $.publish ('onGoogleLoginEvent');

    });

  }

  /**

   * Google事件

   */

  **onGoogleLoginEvent** () {

    **if** (this.googleInfo.isSignedIn) {

      this.googleCallbackHandler (ThirdPartyLogin.getAuthInstance ());//已经登录的回调

    } **else** {

      ThirdPartyLogin.googleSignIn ((res) => {//执行google的登录方法

        //登录成功后的方法

        this.googleCallbackHandler (ThirdPartyLogin.getAuthInstance ());

      }, (err) => {

        console.log (err.error);

      });

    }

  }

  /**

   * google初始化事件

   */

  **onInitGoogleEvent** () {//初始化谷歌事件

    ThirdPartyLogin.onInitGoogle ({}, (res) => {

      console.log ('google init complete...', res);

      let getAuthInstance = ThirdPartyLogin.getAuthInstance ();//获取GoogleAuth对象

      this.googleInfo.isSignedIn = getAuthInstance.isSignedIn.get ();//存储登录状态

    }, **function** (err) {

      return T.toast (err.details);

    });

  }

  /**

   * 谷歌登录成功的回调

   */

  googleCallbackHandler (getAuthInstance) {

    console.log ('登录成功', getAuthInstance);//这个参数是GoogleAuth对象

    this.googleInfo.isSignedIn = getAuthInstance.isSignedIn.get ();//存储登录状态

    console.log(this.googleInfo);

    let GoogleUser = getAuthInstance.currentUser.get ();//这个方法获取返回的响应对象

    console.log ('响应对象：', GoogleUser.getAuthResponse (true));//true参数可以用于获取access_token

  }

}

let platform = new Platform ();

复制代码

**关注下面的标签，发现更多相似文章**