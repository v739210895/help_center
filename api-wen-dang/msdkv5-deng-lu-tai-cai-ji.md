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



API文档参考：[http://docs.msdk.qq.com/v5/zh-CN/Server/verify.html](http://docs.msdk.qq.com/v5/zh-CN/Server/)

