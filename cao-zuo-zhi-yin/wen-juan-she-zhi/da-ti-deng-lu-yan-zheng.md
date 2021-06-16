# 答题登录验证

问卷系统支持采集不同类型的登录态信息（openid），问卷设计者可参考以下流程，开启对应的功能。部分功能需要由开发者对接系统接口实现。

![&#x767B;&#x5F55;&#x6001;&#x83B7;&#x53D6;](../../.gitbook/assets/image%20%28668%29.png)

![&#x767B;&#x5F55;&#x9A8C;&#x8BC1;&#x914D;&#x7F6E;](../../.gitbook/assets/image%20%28670%29.png)

## 微信、QQ登录

功能启用后，问卷系统会自动拉起QQ/微信登录， 用户登录后才允许答题。此处会采集问卷系统用户的uid，在答题数据中记录并显示。

## MSDK v3

功能启用后，在已接入MSDK v3的游戏内投放时，问卷系统可获取已登录用户的openid，并存储在用户id列，在答题数据中显示。

## MSDK v5 

功能启用后，在已接入MSDK v5的游戏内投放时，问卷系统可获取已登录用户的gopenid，并存储在用户id列，在答题数据中显示。

### 参数配置说明

{% hint style="info" %}
“密钥”请填写飞鹰系统参数中的MSDK\_SERVER\_KEY

“msdk域名”区分正式环境和测试环境，填写参考：

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x73AF;&#x5883;&#xFF08;&#x57DF;&#x540D;&#xFF09;</th>
      <th style="text-align:left">HTTP&#x5185;&#x7F51;</th>
      <th style="text-align:left">HTTPS&#x5916;&#x7F51;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x6D4B;&#x8BD5;&#x73AF;&#x5883;</td>
      <td style="text-align:left">http://hktest.itop.tencent-cloud.net</td>
      <td style="text-align:left">
        <p>https://hktest.itop.qq.com &#xFF08;&#x56FD;&#x5185;&#xFF09;</p>
        <p>https://ipv6-hktest.itop.qq.com&#xFF08;&#x6D77;&#x5916;&#xFF09;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x56FD;&#x5185;&#x6B63;&#x5F0F;&#x73AF;&#x5883;</td>
      <td style="text-align:left">http://itop.tencent-cloud.net</td>
      <td style="text-align:left">
        <p>https://itop.qq.com</p>
        <p>https://ipv6-sh.itop.qq.com</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x65B0;&#x52A0;&#x5761;&#x6B63;&#x5F0F;&#x73AF;&#x5883;</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">https://sg.itopsdk.com</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x7845;&#x8C37;&#x6B63;&#x5F0F;&#x73AF;&#x5883;</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">https://us.itopsdk.com</td>
    </tr>
  </tbody>
</table>
{% endhint %}



## INTL登录验证

功能启用后，在已接入INTL的游戏内投放时，问卷系统可获取已登录用户的openid，并存储在用户id列，在答题数据中显示。

### 参数配置说明

{% hint style="info" %}
“密钥”请填写INTL管理端参数中的INTL\_SERVER\_KEY

“域名”区分正式环境和测试环境，填写参考：[INTL域名](https://developers.intlgame.com/docs/unity_zh/Backend/Overall.html#21-%E7%8E%AF%E5%A2%83)
{% endhint %}

## 参数传递（不校验模式）

对于未接入msdk的APP，问卷内嵌投放时，问卷系统通过开发者传递登录态的方式来采集用户的uid。不校验模式开启功能后，只需在问卷链接后直接拼接参数即可把玩家信息等参数传递到问卷系统。

{% hint style="warning" %}
1. 不校验模式不进行签名校验，可能会存在被刷风险
2. 已开启不校验模式的问卷，若未正确拼接openid参数将无法打开问卷
{% endhint %}

![&#x53C2;&#x6570;&#x4F20;&#x9012;&#x63A5;&#x53E3;&#xFF08;&#x4E0D;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#xFF09;](../../.gitbook/assets/image%20%28669%29.png)

{% hint style="info" %}
**【内嵌投放链接】** 

https://in.survey.imur.tencent.com/?sid=5e8d767b76051f46707cf692&lang=zh-CHS&ADTAG=sid.5e8d767b76051f46707cf692&openid=XXXX&source=XXXX&info=XXXX
{% endhint %}

点击“[参数传递接口（不校验模式）](../../api-wen-dang/can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi.md)”查看API文档，了解问卷链接的改造方法。

## 参数传递（严格校验模式）

对于未接入msdk的APP，问卷内嵌投放时，问卷系统通过开发者传递登录态的方式来采集用户的uid。功能开启后，弹窗显示密钥，密钥用于生成签名（密钥可自行修改或重新生成），点击确认关闭弹窗。

![&#x53C2;&#x6570;&#x4F20;&#x9012;&#xFF08;&#x4E25;&#x683C;&#x6821;&#x9A8C;&#xFF09;-&#x914D;&#x7F6E;&#x5BC6;&#x94A5;](../../.gitbook/assets/image%20%28671%29.png)

{% hint style="info" %}
【内嵌投放链接示例】 

https://inapi.survey.imur.tencent.com/autologin?sid=5e8d767b76051f46707cf692&uid=user\_id&timestamp=1573455797&source=dwk&info=extra\_info&redirect=https%3A%2F%2Fin.survey.imur.tencent.com%2F%3Fsid%5e8d767b76051f46707cf692%26lang%3Dzh-CHS%26ADTAG%3Dsid.5e8d767b76051f46707cf692&sign=2ac5ab8ce6a9b306e07dc2664fe7d175
{% endhint %}

点击“[参数传递接口（严格校验）](../../api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou.md)”查看API文档，了解内嵌投放链接的改造方法。

