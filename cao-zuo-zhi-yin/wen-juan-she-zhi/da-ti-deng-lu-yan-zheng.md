# 答题登录验证

问卷系统支持采集不同类型的登录态信息（openid），问卷设计者可参考以下流程，开启对应的功能。部分功能需要由开发者对接系统接口实现。

![登录态获取](<../../.gitbook/assets/image (367).png>)

![登录验证配置](../../.gitbook/assets/Snipaste\_2023-10-08\_14-28-38.png)

## 微信、QQ登录

功能启用后，问卷系统会自动拉起QQ/微信登录， 用户登录后才允许答题。此处会采集问卷系统用户的uid，在答题数据中记录并显示。

## MSDK v3

功能启用后，在已接入MSDK v3的游戏内投放时，问卷系统可获取已登录用户的openid，并存储在用户id列，在答题数据中显示。

![](../../.gitbook/assets/Snipaste\_2023-10-08\_14-30-24.png)

## MSDK v5&#x20;

功能启用后，在已接入MSDK v5的游戏内投放时，问卷系统可获取已登录用户的gopenid，并存储在用户id列，在答题数据中显示。

![](../../.gitbook/assets/Snipaste\_2023-10-08\_14-31-20.png)

### 参数配置说明

{% hint style="info" %}
“密钥”请填写飞鹰系统参数中的MSDK\_SERVER\_KEY

“msdk域名”区分正式环境和测试环境，填写参考：
{% endhint %}

| 环境（域名）  | HTTP内网                               | HTTPS外网                                                                          |
| ------- | ------------------------------------ | -------------------------------------------------------------------------------- |
| 测试环境    | http://hktest.itop.tencent-cloud.net | <p>https://hktest.itop.qq.com （国内）</p><p>https://ipv6-hktest.itop.qq.com（海外）</p> |
| 国内正式环境  | http://itop.tencent-cloud.net        | <p>https://itop.qq.com</p><p>https://ipv6-sh.itop.qq.com</p>                     |
| 新加坡正式环境 | 无                                    | https://sg.itopsdk.com                                                           |
| 硅谷正式环境  | 无                                    | https://us.itopsdk.com                                                           |



## INTL登录验证

功能启用后，在已接入INTL的游戏内投放时，问卷系统可获取已登录用户的openid，并存储在用户id列，在答题数据中显示。

![](../../.gitbook/assets/Snipaste\_2023-10-08\_14-32-06.png)

### 参数配置说明

{% hint style="info" %}
“密钥”请填写INTL管理端参数中的INTL\_SERVER\_KEY

“域名”区分正式环境和测试环境，填写参考：[INTL域名](https://developers.intlgame.com/docs/intlsdk/JS/JSOverview#Environment)
{% endhint %}

## 参数传递（不校验模式）

对于未接入msdk的APP，问卷内嵌投放时，问卷系统通过开发者传递登录态的方式来采集用户的uid。不校验模式开启功能后，只需在问卷链接后直接拼接参数即可把玩家信息等参数传递到问卷系统。

{% hint style="warning" %}
1. 不校验模式不进行签名校验，可能会存在被刷风险
2. 已开启不校验模式的问卷，若未正确拼接openid参数将无法打开问卷
{% endhint %}

![参数传递接口（不校验模式）](../../.gitbook/assets/Snipaste\_2023-10-08\_14-32-51.png)

{% hint style="info" %}
**【内嵌投放链接】**&#x20;

https://in.survey.imur.tencent.com/?sid=5e8d767b76051f46707cf692\&lang=zh-CHS\&ADTAG=sid.5e8d767b76051f46707cf692\&openid=XXXX\&source=XXXX\&info=XXXX
{% endhint %}

点击“[参数传递接口（不校验模式）](../../api-wen-dang/can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi.md)”查看API文档，了解问卷链接的改造方法。

## 参数传递（严格校验模式）

对于未接入msdk的APP，问卷内嵌投放时，问卷系统通过开发者传递登录态的方式来采集用户的uid。功能开启后，弹窗显示密钥，密钥用于生成签名（密钥可自行修改或重新生成），点击确认关闭弹窗。

![参数传递（严格校验）-配置密钥](../../.gitbook/assets/Snipaste\_2023-10-08\_14-34-26.png)

{% hint style="info" %}
【内嵌投放链接示例】&#x20;

https://inapi.survey.imur.tencent.com/autologin?sid=5e8d767b76051f46707cf692\&uid=user\_id\&timestamp=1573455797\&source=dwk\&info=extra\_info\&redirect=https%3A%2F%2Fin.survey.imur.tencent.com%2F%3Fsid%5e8d767b76051f46707cf692%26lang%3Dzh-CHS%26ADTAG%3Dsid.5e8d767b76051f46707cf692\&sign=2ac5ab8ce6a9b306e07dc2664fe7d175
{% endhint %}

点击“[参数传递接口（严格校验）](../../api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou.md)”查看API文档，了解内嵌投放链接的改造方法。
