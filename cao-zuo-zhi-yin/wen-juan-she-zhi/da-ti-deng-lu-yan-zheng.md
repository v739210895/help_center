# 答题登录验证

问卷系统支持采集不同类型的登录态，问卷设计者可参考以下流程，开启对应的功能。部分功能需要由开发者对接系统接口实现。

![](../../.gitbook/assets/image%20%28668%29.png)

## 微信、QQ登录验证

功能启用后，非MSDK内嵌投放时，问卷系统会自动拉起QQ/微信登录， 用户登录后才允许答题。此处会采集问卷系统用户的uid，在答题数据中记录并显示。

## MSDK/INTL登录验证

功能启用后，对于接入了msdk [v3](https://imur.gitbook.io/help_center/api-wen-dang/msdkv3-deng-lu-tai-cai-ji)/[v5](https://imur.gitbook.io/help_center/api-wen-dang/msdkv5-deng-lu-tai-cai-ji)或INTL的APP，问卷内嵌投放时，问卷系统会采集用户的openid（msdk v5采集gopenid），并存储在用户id列，在答题数据中显示。

{% hint style="info" %}
配置msdk v5登录态获取的参数中，“密钥”请填写飞鹰系统参数中的MSDK\_SERVER\_KEY

配置INTL登录态获取的参数中，“密钥”请填写INTL系统参数中的INTL\_SERVER\_KEY
{% endhint %}

## MSDK/INTL登录验证

功能启用后，对于接入了msdk [v3](https://imur.gitbook.io/help_center/api-wen-dang/msdkv3-deng-lu-tai-cai-ji)/[v5](https://imur.gitbook.io/help_center/api-wen-dang/msdkv5-deng-lu-tai-cai-ji)或INTL的APP，问卷内嵌投放时，问卷系统会采集用户的openid（msdk v5采集gopenid），并存储在用户id列，在答题数据中显示。

{% hint style="info" %}
配置msdk v5登录态获取的参数中，“密钥”请填写飞鹰系统参数中的MSDK\_SERVER\_KEY

配置INTL登录态获取的参数中，“密钥”请填写INTL系统参数中的INTL\_SERVER\_KEY
{% endhint %}



