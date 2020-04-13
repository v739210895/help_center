# MSDK-V3登录态采集

对接了MSDK V3版本的APP，可在问卷设置中启用【MSDK登录验证】功能，选择版本为v3；用户提交问卷时，问卷系统会自动获取MSDK的登录态并存储在答题数据中。

![](../.gitbook/assets/image%20%28282%29.png)

{% hint style="info" %}
解密MSDK-V3登录态说明
{% endhint %}

API文档参考：[https://wiki.ssl.msdk.qq.com/Unity/webview.html\#Unity\_DecodeLoginInfo ](https://wiki.ssl.msdk.qq.com/Unity/webview.html#Unity_DecodeLoginInfo%20)

MSDK-V3版本的参数示例如下：

其中msdkEncodeParam参数是V3版本最重要的标识，存储了用户信息与access\_token。

```text
http://www.qq.com?algorithm=v2&version=2.0.6a&timestamp=1423538227203&appid=100703379&sig=427291da31b56b597
39be6da61d433ec&encode=2&msdkEncodeParam=BAD8B1625CB04523B06AAF6739ACB3CEA96F54393831AF5C6890E92EE61CF1A29F
493710592DD84B47D4217BA9FA9DAFB8025CEB27E45EC958689A794E8BD33CF2544CC5D00FCE03AEF7B23EE2BFCA4332F5D69547477
A3E93E44F3270F19664D5499CA2990BE5BA9E232036197B184F1411B76CF95537AC07E3D6A27F054AD3F26648B18554F9C1
```

若系统无法获取正确的登录态时，会显示以下警告弹窗。

（1）游戏调用问卷时，msdkEncodeParam参数缺失或检验失败，会提示该弹窗。

（2）非标准MSDK V3环境中打开时，如游戏外，会提示该弹窗。

![](../.gitbook/assets/image%20%28292%29.png)





