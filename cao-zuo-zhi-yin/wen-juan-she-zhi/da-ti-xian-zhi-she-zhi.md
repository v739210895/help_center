# 答题限制设置

问卷系统支持采集不同类型的登录态，问卷设计者可参考以下流程，开启对应的功能。部分功能需要由开发者对接系统接口实现。

![](../../.gitbook/assets/image%20%2814%29.png)

![&#x7B54;&#x9898;&#x9650;&#x5236;&#x8BBE;&#x7F6E;](../../.gitbook/assets/image%20%28200%29.png)

## 微信、QQ登录验证

功能启用后，非MSDK内嵌投放时，问卷系统会自动拉起QQ/微信登录， 用户登录后才允许答题。此处会采集问卷系统用户的uid，在答题数据中记录并显示。

## MSDK登录验证

功能启用后，对于接入了msdk [v3](https://imur.gitbook.io/help_center/api-wen-dang/msdkv3-deng-lu-tai-cai-ji)或[v5](https://imur.gitbook.io/help_center/api-wen-dang/msdkv5-deng-lu-tai-cai-ji)的APP，问卷内嵌投放时，问卷系统会采集用户的openid，将openid解析并存储在uid列，在答题数据中显示。

{% hint style="info" %}
配置msdk v5登录态获取的参数中，“密钥”请填写飞鹰系统参数中的MSDK\_SERVER\_KEY
{% endhint %}

## 每个账号只能回答一次

此功能需要配合微信、QQ登录验证或MSDK登录验证使用，功能启用后，若该用户已回答过问卷，会禁止用户二次回答。

![&#x91CD;&#x590D;&#x7B54;&#x9898;&#x63D0;&#x793A;](../../.gitbook/assets/image%20%28384%29.png)

## 每个IP只能答一次

{% hint style="danger" %}
功能暂未开放使用
{% endhint %}

功能启用后，打开问卷时会根据用户IP进行校验，若该用户已回答过问卷，会禁止用户二次回答。

## 每个浏览器只能答一次

{% hint style="danger" %}
功能暂未开放使用
{% endhint %}

功能启用后，打开问卷时会根据用户的浏览器进行校验，若该用户已回答过问卷，会禁止用户二次回答。

