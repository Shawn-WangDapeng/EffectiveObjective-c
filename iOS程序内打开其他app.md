##iOS程序内打开其它app
在iOS内部打开其他应用，使用openUrl来实现。下面介绍打开其它应用的方法：

* 打开浏览器
* 打开email
* 拨号程序
* 短信
* 打开第三方应用  
  
**打开浏览器：**  

	格式 mailto://${mailaddress}
	[[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"mailto://username@126.com"]];
**打开拨号：**

	格式 tel://:${phonenumber}
	 [[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"tel://8888888"]];
**打开短息：**

	格式 sms:${phonenumber}
	[[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"sms:888888"]];
**打开其他三方应用：**
比如我创建了一个应用A，现在又创建了一个应用B，我想在B应用中打开应用A，首先我在应用A的info.list中设置URL identifier一个名字为abc，
![](http://7xleoh.com1.z0.glb.clouddn.com/URLidentifier.png)
然后在应用B中调用方法为：  

```
[[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"abc://"]];
//在打开应用直线可以用canOpenURL方法来判断是否能够打开该应用,该方法返回一个布尔类型
[[UIApplication sharedApplication] canOpenURL:myUrl]
```  

在这里要注意在iOS9以前在知道要打开应用的identifier即可。但是在iOS9以后苹果做了安全性限制，所以要在info.list中的LSApplicationQueriesSchemes中把要打开的三方应用加入白名单。不然不能打开。
![](http://7xleoh.com1.z0.glb.clouddn.com/LSApplicationQueries.png)