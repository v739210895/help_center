# 为什么会接收到文档中未说明的回调参数

在问卷链接后注入的参数会在回调时同步回调到开发者服务端，导致开发者服务端接收到文档中未说明的回调参数。

常见场景包括：

* MSDK登录时，浏览器会自动在问卷链接后注入玩家的登录态信息
* 客户端在问卷链接后注入自定义参数
* 参数传递（严格校验模式）/（不校验模式）中，要求注入玩家id等登录态参数

{% hint style="info" %}
**特别说明：**

1. 非必传参数有值时参与加密，未传则不参与加密
2. [登录态回调参数说明文档](../api-wen-dang/deng-lu-tai-hui-tiao-jie-kou.md#can-shu-shuo-ming)未说明的参数不参与加密
3. 如使用MSDK v3/v5、INTL自动登录，info仅作为普通参数透传，不参与加密，也不采集到答案中。
{% endhint %}

![&#x53C2;&#x4E0E;&#x52A0;&#x5BC6;&#x7684;&#x56DE;&#x8C03;&#x53C2;&#x6570;](../.gitbook/assets/image%20%28684%29.png)



## Why do I receive callback parameters that are not specified in the document?

The parameters injected after the questionnaire link will be synchronously called back to the developer server during the callback, causing the developer server to receive callback parameters that are not described in the document. 

Common scenarios include:

* When logging in to MSDK, the browser will automatically inject the player's login status information after the questionnaire link 
* The client injects custom parameters after the questionnaire link 
* In parameter transfer \(strict verification mode\)/\(non-verification mode\), login parameters such as player id are required to be injected

{% hint style="info" %}
**Special Note:**

1. Participate in encryption when the optional parameter has a value, and not participate in

   encryption if it is not passed

2. [Callback Interface](../api-docs/callback-interface.md) documentation unspecified parameters is not involved in

   encryption

3. If you use MSDK v3/v5, INTL to log in automatically, info is only transparently transmitted

   as a common parameter, and does not participate in encryption, nor is it collected in the

   answer.
{% endhint %}



\*\*\*\*

