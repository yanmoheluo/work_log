因为部分业务使用的微软的bing的翻译

API：http://api.microsofttranslator.com/V2/[Ajax](https://so.csdn.net/so/search?q=Ajax&spm=1001.2101.3001.7020).svc/Translate  

sample:

```html
http://api.microsofttranslator.com/V2/Ajax.svc/Translate?oncomplete=mycallback1412835995529&appId=A4D660A48A6A97CCA791C34935E4C02BBB1BEC1C&from=&to=zh-cn&text=Guten%20Abend
```

  
因为appID数量收到限制，我们需要自己申请一个appID，过程如下：

 **step1：** 

           打开 [https://datamarket.azure.com/dataset/bing/microsofttranslator](https://datamarket.azure.com/dataset/bing/microsofttranslator)     点击活动订阅下面的购买

![](https://img-blog.csdn.net/20141009163413953?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGlsaWVuMTAxMA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)  

  

 **step2：**   
  
                打开  https://datamarket.azure.com/developer/applications/register  注册app 填写 client_id

                                              ![](https://img-blog.csdn.net/20141009163844132?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGlsaWVuMTAxMA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)  
  

得到你的 客户端ID: hellowodbaby  , 客户端秘钥:Pc2PqzjqxdeaZYb5KDrKdouzN7j8s5At5BBFXBRJoU0= .

       打开 https://datamarket.azure.com/developer/applications 你会看到你注册的

![](https://img-blog.csdn.net/20141009163916656?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGlsaWVuMTAxMA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)  

  

  

```php
    /*     * Get the access token.     *     * @param string $grantType    Grant type.     * @param string $scopeUrl     Application Scope URL.     * @param string $clientID     Application client ID.     * @param string $clientSecret Application client ID.     * @param string $authUrl      Oauth Url.     *     * @return string.     */     function getTokens($grantType, $scopeUrl, $clientID, $clientSecret, $authUrl){           try {            //Initialize the Curl Session.            $ch = curl_init();            //Create the request Array.            $paramArr = array (                                    'grant_type'    => $grantType,                 'scope'         => $scopeUrl,                 'client_id'     => $clientID,                 'client_secret' => $clientSecret            );            //Create an Http Query.//            $paramArr = http_build_query($paramArr);            //Set the Curl URL.            curl_setopt($ch, CURLOPT_URL, $authUrl);            //Set HTTP POST Request.            curl_setopt($ch, CURLOPT_POST, TRUE);            //Set data to POST in HTTP "POST" Operation.            curl_setopt($ch, CURLOPT_POSTFIELDS, $paramArr);            //CURLOPT_RETURNTRANSFER- TRUE to return the transfer as a string of the return value of curl_exec().            curl_setopt ($ch, CURLOPT_RETURNTRANSFER, TRUE);            //CURLOPT_SSL_VERIFYPEER- Set FALSE to stop cURL from verifying the peer's certificate.            curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);            //Execute the  cURL session.            $strResponse = curl_exec($ch);            //Get the Error Code returned by Curl.            $curlErrno = curl_errno($ch);            if($curlErrno){                $curlError = curl_error($ch);                throw new Exception($curlError);            }            //Close the Curl Session.            curl_close($ch);            //Decode the returned JSON string.            $objResponse = json_decode($strResponse,true);			var_dump($objResponse);            if (isset($objResponse['error'])){                throw new Exception($objResponse['error_description']);				return FALSE;            }            return $objResponse['access_token'];        } catch (Exception $e) {            echo "Exception-".$e->getMessage();			return FALSE;        }    }
```

  
 

```php
	//Client ID of the application.	$clientID       = "hellowodbaby";	//Client Secret key of the application.	$clientSecret = "Pc2PqzjqxdeaZYb5KDrKdouzN7j8s5At5BBFXBRJoU0=";    //OAuth Url.    $authUrl      = "https://datamarket.accesscontrol.windows.net/v2/OAuth2-13/";    //Application Scope Url    $scopeUrl     = "http://api.microsofttranslator.com";    //Application grant type    $grantType    = "client_credentials";     $authObj      = new AccessTokenAuthentication();    //Get the Access token.    $accessToken  = $authObj->getTokens($grantType, $scopeUrl, $clientID, $clientSecret, $authUrl);    	var_dump("bearer%20".urlencode($accessToken) );    //上面输出的就是 appid，这个appid每隔expires_in秒会变掉【在数组$objResponse 】，注意。
```

  

  

 参考 

http://msdn.microsoft.com/en-us/library/ff512385.aspx  
  
http://msdn.microsoft.com/en-us/library/hh454950.aspx