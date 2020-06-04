# MSDK-V5登录态采集

对接了MSDK V5版本的APP，可在问卷设置中启用【MSDK登录验证】功能，选择版本为v5；用户提交问卷时，问卷系统会自动获取MSDK的登录态并存储在答题数据中。

![&#x914D;&#x7F6E;MSDK v5&#x767B;&#x5F55;&#x6001;&#x83B7;&#x53D6;&#x63A5;&#x5165;&#x6240;&#x9700;&#x8981;&#x7684;&#x53C2;&#x6570;](../.gitbook/assets/image%20%28358%29.png)

{% hint style="info" %}
“密钥”请填写飞鹰系统参数中的MSDK\_SERVER\_KEY

“msdk域名”区分正式环境和测试环境，填写参考：

| 环境（域名） | HTTP内网 | HTTPS外网 |
| :--- | :--- | :--- |
| 测试环境 | hktest.itop.tencent-cloud.net | hktest.itop.qq.com |
| 国内正式环境 | itop.tencent-cloud.net | itop.qq.com / ipv6-sh.itop.qq.com |
| 新加坡正式环境 | 无 | sg.itopsdk.com |
| 硅谷正式环境 | 无 | us.itopsdk.com |
{% endhint %}



{% hint style="info" %}
解密MSDK-V5登录态说明
{% endhint %}

API文档1参考：[http://docs.msdk.qq.com/v5/zh-CN/Server/verify.html](http://docs.msdk.qq.com/v5/zh-CN/Server/)

API文档2参考：[http://docs.msdk.qq.com/v5/zh-CN/Server/verify.html](http://docs.msdk.qq.com/v5/zh-CN/Server/verify.html)

（1）系统使用itopencodeparam参数进行登录态解密，此时要求必须带上os、gameid、channelid、ts、sig、source这6个参数参与，示例如下：

```text
https://hktest.itop.qq.com/v2/auth/decrypt?channelid=1&gameid=11&os=1&source=0&ts=1529907080&sig=8279b3214fc4900e7551ee21593b4d80&itopencodeparam=d9b48147c3b809a2bebbd8b2e96c26f1
```



{% hint style="info" %}
登录失败提示
{% endhint %}

当系统无法获取正确的登录态时，会显示警告弹窗，主要导致失败的原因如下：

（1）itopencodeparam解密登录态时，由于缺失os、gameid、channelid、ts、sig、source等参数导致解密失败。

![](../.gitbook/assets/image%20%28293%29.png)



{% hint style="warning" %}
如MSDK-V3登录态采集接口联调失败，可改用参数传递（[严格校验模式](https://imur.gitbook.io/help_center/api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou)、[不校验模式](https://imur.gitbook.io/help_center/api-wen-dang/can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)）接口，实现登录态传递。
{% endhint %}

