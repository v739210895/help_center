# INTL登录态采集

对接了INTL的APP，可在问卷设置中启用【MSDK登录验证】功能，选择版本为**INTL**；用户提交问卷时，问卷系统会自动获取该玩家登录态并存储在答题数据中。

![&#x914D;&#x7F6E;INTL&#x767B;&#x5F55;&#x6001;&#x83B7;&#x53D6;&#x63A5;&#x5165;&#x6240;&#x9700;&#x8981;&#x7684;&#x53C2;&#x6570;](../.gitbook/assets/image%20%28657%29.png)

### 参数配置说明

{% hint style="info" %}
“密钥”请填写飞鹰系统参数中的INTL\_SERVER\_KEY

“域名”区分正式环境和测试环境，填写参考：[INTL域名](https://developers.intlgame.com/docs/unity_zh/Backend/Overall.html#21-%E7%8E%AF%E5%A2%83)
{% endhint %}



### 解密INTL登录态说明

API文档1参考：[https://developers.intlgame.com/docs/unity\_zh/Module/WebView.html\#23-%E8%8E%B7%E5%8F%96%E5%8A%A0%E5%AF%86%E7%A5%A8%E6%8D%AE](https://developers.intlgame.com/docs/unity_zh/Module/WebView.html#23-%E8%8E%B7%E5%8F%96%E5%8A%A0%E5%AF%86%E7%A5%A8%E6%8D%AE)

API文档2参考：[http://docs.msdk.qq.com/v5/zh-CN/Server/verify.html](https://developers.intlgame.com/docs/unity_zh/Backend/Auth.html#%E4%BA%8C%E3%80%81%E8%A7%A3%E5%AF%86%E6%A0%A1%E9%AA%8C)

（1）系统使用encodeparam参数进行登录态解密，此时要求必须带上os、gameid、channelid、ts、sig、source这6个参数参与，示例如下：

```text
https://www.youtube.com/?gameid=11&os=1&ts=1597840414&version=0.1.000.0001&seq=11-42e0e9d2-2f0e-4b01-a1ab-6831cf9b6165-1597840414-11&encodeparam=4060E2A762B31B8B57A8D5A9BBAF10E8657A5A3A285B0DA7159417C2D6F0D801
```

### 登录失败提示

当系统无法获取正确的登录态时，会显示警告弹窗，主要导致失败的原因如下：

（1）encodeparam解密登录态时，由于缺失os、gameid、channelid、ts、sig、source等参数导致解密失败。

![&#x767B;&#x5F55;&#x5931;&#x8D25;](../.gitbook/assets/image%20%28293%29.png)

{% hint style="warning" %}
如INTL登录态采集接口联调失败，可改用参数传递（[严格校验模式](https://imur.gitbook.io/help_center/api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou)、[不校验模式](https://imur.gitbook.io/help_center/api-wen-dang/can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)）接口，实现登录态传递。
{% endhint %}

