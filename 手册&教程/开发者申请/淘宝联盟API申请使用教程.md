**API是什么？**

[API](https://so.csdn.net/so/search?q=API&spm=1001.2101.3001.7020)是一种接口，提供给淘客通过输入某些信息，来输出对应的淘宝联盟提供的某些信息和某种服务的一个通道。

**API如何使用？**

淘宝联盟的API都通过淘宝开放平台做开放输出。使用API需要分4步。

- **一、网站/APP备案**

要使用API必须要网站或者APP 备案。

进入联盟后台，点击**推广管理—>网站管理**—>**新增网站推广**; 根据页面引导，填写备案信息，等待审核。

- **二、申请APPKEY**

申请APPKEY: 网站审核通过后，点击 **查看权限—>申请权限**  ，申请需要的 APPKEY。按点击“申请权限”会跳到“阿里开放平台”，按流程操作即可。

![](https://img-blog.csdnimg.cn/img_convert/0235abc295e4907c47b706db88f387f5.png)

**查看APPKEY:** 申请成功后，在网站/APP管理相应位置查看。

![](https://img-blog.csdnimg.cn/img_convert/312818d103e323b26c9170d6c3b8acf1.png)

**三、下载SDK**

要使用API，必须先下载阿里开放平台的SDK。SDK提供调用API的功能包，封装了API请求方法，用于集成到服务端程序中，获取相关数据使用。从联盟APP 备案网站下的APPKEY信息右侧点击“查看”就可到阿里开放平台下载SDK。

       如下图，根据实际情况选择对应的版本。

![](https://img-blog.csdnimg.cn/img_convert/43c5532f6d7e1e51dd7d9cab8eae091b.png)

**四、使用API**

接下来就可以根据需要使用的API说明文档来使用API啦。

请求参数为入参，响应参数为出参。

![](https://img-blog.csdnimg.cn/img_convert/2165a5e33a7d5d3891bc84f435aa9891.png)

 adzoneID，备案网站（site id）和APPKEY三者必须配套，才可正常调用。如果APPKEY和adzoneID不匹配或传递参数错误，会不算淘客交易或者取无法正常调用。

![](https://img-blog.csdnimg.cn/img_convert/caf1786c43c18d8dac768a65c376c996.png)

F&Q

**1.API的调用量是多少？**

单一API没有调用量限制，但是阿里开放平台对APP证书的调用量进行了限制，默认为10W/天，可以进入自己的TOP平台进行查询。当当日调用量超过90%时，可申请自助提升调用量（提升量仅当日有效）。

![](https://img-blog.csdnimg.cn/img_convert/65fa23dee403e138815fa1e4f5d171a7.png)

2、传参错误：

使用中API中， adzoneID，备案网站（site id）和APPKEY三者必须配套，才可正常调用。如果APPKEY和adzoneID不匹配或传递参数错误，会不算淘客交易或者取无法正常调用。

![](https://img-blog.csdnimg.cn/img_convert/c3e0ea22206d52917476b72e1c222df7.png)