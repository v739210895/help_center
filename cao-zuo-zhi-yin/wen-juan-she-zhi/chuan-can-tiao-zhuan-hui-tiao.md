# 传参/跳转/回调

问卷系统支持内嵌投放及参数传递、答题后跳转、参数回调等功能，用户可根据实际需要按以下各项设置。

![&#x4F20;&#x53C2;/&#x8DF3;&#x8F6C;/&#x56DE;&#x8C03;](../../.gitbook/assets/image%20%28285%29.png)

## 非MSDK登录态传递接口

对于未接入msdk的APP，问卷内嵌投放时，问卷系统通过开发者传递登录态的方式来采集用户的uid。功能开启后，弹窗显示密钥，密钥用于生成签名（密钥可自行修改或重新生成），点击确认关闭弹窗。

![&#x914D;&#x7F6E;&#x5BC6;&#x94A5;](../../.gitbook/assets/image%20%2813%29.png)

{% hint style="warning" %}
### 请求url示例

API接口地址?sid=XX&uid=XX&timestamp=XX&source=XX&info=XX&redirect=问卷投放链接&sign=XX
{% endhint %}

[点击了解详细API文档](../../api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou.md)。

## 提交问卷跳转到指定页面

功能开启后，在设置弹窗中填写跳转的链接（链接需为包含http://或http://前缀的地址），设置完成后当答题者提交问卷后浏览器将跳转到您设置的链接上。

![&#x8BBE;&#x7F6E;&#x8DF3;&#x8F6C;&#x5730;&#x5740;](../../.gitbook/assets/image%20%28301%29.png)

## 登录态回调接口

提供登录态回调的功能，开发者可自行配置回调地址和密钥，问卷系统将登录态等参数回调给开发者，开发者获取参数后可用于奖励发放。

![&#x914D;&#x7F6E;&#x767B;&#x5F55;&#x6001;&#x56DE;&#x8C03;](../../.gitbook/assets/image%20%28263%29.png)



{% hint style="info" %}
### 回调url示例

开发者回调接口url?sid=5da414769e8aa80019305e32×tamp=1573556685&uid=test\_user&user\_type=third\_party&uid\_source=qq&info=afdadsfasdfasdf&callback\_params=callbackparams&sign=38408d6222e1a4c6fa598e4820443ca8
{% endhint %}

[点击了解详细API文档](../../api-wen-dang/deng-lu-tai-hui-tiao-jie-kou.md)。

## API调用

