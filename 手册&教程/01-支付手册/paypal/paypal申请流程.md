# paypal开发者账户申请步骤
网上很多关于如何申请paypal开发者账号的说明，都是很久以前的文档，所以多少会和现有的情况产生冲突，下面就2014年11月5日仍然适用的申请方法做一些总结

1 开发者账号的申请

网址： [https://developer.paypal.com/](https://developer.paypal.com/) （点击右上角的“sign up”）

请注意，这是开发者账号，所以肯定是未通过认证的，通过认证需要绑定信用卡之类的，我想没有程序员希望在开发的时候把自己的信用卡或者银行卡贡献出去吧。

2 在开发者账号下申请测试使用sandbox账户（这一步最关键）

网上已经失效的说明就是出现在这一步

A 当你用刚才申请过的账号登陆完并回到首页之后，请点击"Dashboard"，如下图所示

![](https://img-blog.csdn.net/20141107154158203?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcWluZ2hlZ3U2ODk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)  

![](https://blog.csdn.net/qinghegu689/article/details/40820585?ops_request_misc=&request_id=&biz_id=102&utm_term=paypal%E5%BC%80%E5%8F%91%E8%80%85%E7%94%B3%E8%AF%B7%E6%B5%81%E7%A8%8B&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-40820585.142^v88^insert_down1,239^v2^insert_chatgpt&spm=1018.2226.3001.4187)  

  

系统默认生成两个与你之前同类型邮箱的账户，包括个人账户以及商家账户，我的建议是自己重新申请。

B 申请sandbox账号

需要注意，如果你的开发者账号是用qq之类非国际化或者不够国际化的邮箱申请是没有问题的，但是在开发者账号之下申请测试用的sandbox个人和企业账号的时候建议使用yahoo,gmail,hotmail等邮箱

C 点击“Create Account”进行sandbox的申请

3 sandbox测试账号的的相关设置

网址： [https://www.sandbox.paypal.com](https://www.sandbox.paypal.xn--com%28sandbox%29-lm5s4p89iuwvoqc4ln3fbzvooaf49ew1aca232u2iqv25jsrhg00e83we3pac701hu34f/) 

完成第2步之后，用你刚刚申请好的买家和卖家在这个网站上登陆查看并进行相关设置

![](https://img-blog.csdn.net/20141107154325917?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcWluZ2hlZ3U2ODk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)  

![](https://blog.csdn.net/qinghegu689/article/details/40820585?ops_request_misc=&request_id=&biz_id=102&utm_term=paypal%E5%BC%80%E5%8F%91%E8%80%85%E7%94%B3%E8%AF%B7%E6%B5%81%E7%A8%8B&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-40820585.142^v88^insert_down1,239^v2^insert_chatgpt&spm=1018.2226.3001.4187)  

  

可以看到测试账号显示的是已经认证的状态，如果想切换测试账号点击“退出”，而不是右上角开发者账号的“登出”，下面是卖家账号，可以看到买家对他进行的付款操作已经完成了，初始的余额都是9999999，也即1000万少一元

![](https://img-blog.csdn.net/20141107154458984?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcWluZ2hlZ3U2ODk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)  

  

![](https://blog.csdn.net/qinghegu689/article/details/40820585?ops_request_misc=&request_id=&biz_id=102&utm_term=paypal%E5%BC%80%E5%8F%91%E8%80%85%E7%94%B3%E8%AF%B7%E6%B5%81%E7%A8%8B&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-40820585.142^v88^insert_down1,239^v2^insert_chatgpt&spm=1018.2226.3001.4187)  

（以下只针对卖家）

A 点击“用户信息”，在出现的三列中选择“账户信息”列的“API访问”，就可以完成API访问申请，结果如下

![](https://img-blog.csdn.net/20141107154444603?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcWluZ2hlZ3U2ODk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)  

![](https://blog.csdn.net/qinghegu689/article/details/40820585?ops_request_misc=&request_id=&biz_id=102&utm_term=paypal%E5%BC%80%E5%8F%91%E8%80%85%E7%94%B3%E8%AF%B7%E6%B5%81%E7%A8%8B&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-40820585.142^v88^insert_down1,239^v2^insert_chatgpt&spm=1018.2226.3001.4187)  

  

B 点击“卖家习惯设定”列的“即时付款通知习惯设定”，看结果

![](https://img-blog.csdn.net/20141107154457817?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcWluZ2hlZ3U2ODk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)  

![](https://blog.csdn.net/qinghegu689/article/details/40820585?ops_request_misc=&request_id=&biz_id=102&utm_term=paypal%E5%BC%80%E5%8F%91%E8%80%85%E7%94%B3%E8%AF%B7%E6%B5%81%E7%A8%8B&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-40820585.142^v88^insert_down1,239^v2^insert_chatgpt&spm=1018.2226.3001.4187)  

  

C 点击“卖家习惯设定”列的“网站付款习惯设定”，保存自己所需要的设定

  

至此所有paypal开发所需的内容都已完成，你可以联系客户获取接口进行项目开发了。