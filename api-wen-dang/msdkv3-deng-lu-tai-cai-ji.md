# MSDK-V3登录态采集

对接了MSDK V3版本的APP，可在问卷设置中启用【MSDK登录验证】功能，选择版本为v3；

用户提交问卷时，问卷系统会自动获取MSDK的登录态并存储在答题数据中。

![](../.gitbook/assets/image%20%28283%29.png)

{% hint style="info" %}
解密MSDK-V3登录态说明
{% endhint %}

API文档参考：[https://wiki.ssl.msdk.qq.com/Unity/webview.html\#Unity\_DecodeLoginInfo ](https://wiki.ssl.msdk.qq.com/Unity/webview.html#Unity_DecodeLoginInfo%20)

（1）系统优先使用msdkEncodeParam参数进行登录态解密，此时要求必须带上timestamp、appid、algorithm、version、sig、encode这6个参数参与，示例如下：

```text
http://www.qq.com?algorithm=v2&version=2.0.6a&timestamp=1423538227203&appid=100703379&sig=427291da31b56b597
39be6da61d433ec&encode=2&msdkEncodeParam=BAD8B1625CB04523B06AAF6739ACB3CEA96F54393831AF5C6890E92EE61CF1A29F
493710592DD84B47D4217BA9FA9DAFB8025CEB27E45EC958689A794E8BD33CF2544CC5D00FCE03AEF7B23EE2BFCA4332F5D69547477
A3E93E44F3270F19664D5499CA2990BE5BA9E232036197B184F1411B76CF95537AC07E3D6A27F054AD3F26648B18554F9C1
```

![](../.gitbook/assets/image%20%28488%29.png)

（2）当msdkEncodeParam参数无法正常解密登录态时，系统会直接获取openid参数值作为登录态。

{% hint style="info" %}
登录失败提示
{% endhint %}

当系统无法获取正确的登录态时，会显示警告弹窗，主要导致失败的原因如下：

（1）msdkEncodeParam解密登录态时，由于缺失timestamp、appid、algorithm、version、sig、encode等参数导致解密失败。

（2）链接中无openid参数，导致无法获取登录态。

![](../.gitbook/assets/image%20%28293%29.png)



{% hint style="warning" %}
如MSDK-V3登录态采集接口联调失败，可改用参数传递（[严格校验模式](https://imur.gitbook.io/help_center/api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou)、[不校验模式](https://imur.gitbook.io/help_center/api-wen-dang/can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)）接口，实现登录态传递。
{% endhint %}



