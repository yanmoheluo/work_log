1.首页图片和列表页面。压缩一下，现在图片太大，影响网站速度 鼠标放到图片上现在对应的名称，产品标题或者获取到名称
2.站点地图
3.爬虫文件修改。运行谷歌抓取
4.产品详情页面，把网站名称调用产品标题。
5.过多的css文件整合style
6.https://www.betteryoyo.com/ru把翻译调用文件直接修改成类似前面的链接，？/去除了。
https://www.betteryoyo.com手机访问页面压缩了。调整一下，能正常访问即可
7.https://www.betteryoyo.com/Tao/list1?url=T恤把有URL变成下面的形式。
https://www.betteryoyo.com/Tao/t-shirt。

8.面包屑导  详情页
9.h1标签列表页面调用搜索的关键词， 商品详情页面H1调用标题， 页面只用一个H1 。其他的去除了。商品详情页面网站名称调用对应的产品标题
10.https://www.betteryoyo.com/Tao/view?id=608876251396这链接结构换成下面的这种
https://www.betteryoyo.com/Tao/608876251396
11.<link rel="canonical" href="https://www.betteryoyo.com/Tao/608876251396" />添加标签
12.自定404页面，保留顶部，和地址，中间显示404错误
13.点击产品如果提示下架的时候跳转到上一级。提示加入到语言包做对应的翻译
14.没有移动端的情况下，可以参考这个文档，做网页的viewport配置
https://blog.csdn.net/u013148287/article/details/53510535

大类页面的布局规则	
title规则	Women's Tops Taobao English Shop Online, Buy at Cheap Price & Fast Delivery
description规则	Buy Women's Tops at Taobao English version website with cheap price and fast delivery service at Betteryoyo.com. We are your buying agent and can find, purchase, view and deliver items from our Taobao English website. Buy Women's Tops and ship today!
keywords	women's tops, taobao women's tops, cheap women's tops, buy women's tops

Schema 格式化数据参考
1.在每个页面<head>添加一段固定格式的script信息
'<script type="application/ld+json">'
    .'{
		"@context": "http://schema.org",
		"@type": "Organization",
		"url": "'.$host.'",
		"logo": "'.$host.'{$setting.logo}",
		"address": {
		    "@type": "PostalAddress",
		    "addressLocality": "'.$contact['addresslocality'].'",
		    "addressRegion": "'.$contact['addressregion'].'",
		    "streetAddress": "'.$contact['streetaddress'].'",
		    "postalCode": "'.$contact['postalcode'].'"
	  	},
		"contactPoint" : [{
			"@type" 		: "ContactPoint",
			"telephone" 	: "'.$contact['tel'].'",
			"contactType" 	: "customer service",
			"areaServed"	: "'.$contact['areaserved'].'",
			"availableLanguage" : [
		      	"English"
		    ]
		}],
		"sameAs" : [ //社交网站地址
	        '.($contact['twitter'] ? '"'.$contact['twitter'].'",' : '').'
	        '.($contact['facebook'] ? '"'.$contact['facebook'].'",' : '').'
	        '.($contact['linkedin'] ? '"'.$contact['linkedin'].'",' : '').'
	        '.($contact['pinterest'] ? '"'.$contact['pinterest'].'",' : '').
		 ]
		
    }
    
    </script>';
2.在产品页面面包屑导航schema
参考格式如下图：
