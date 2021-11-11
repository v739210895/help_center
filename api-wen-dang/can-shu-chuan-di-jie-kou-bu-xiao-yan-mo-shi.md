# 参数传递接口（不校验模式）

### 接口说明

#### 接口定义

参数传递接口（不校验模式）接口用于解决（1）第三方开发者拥有自己系统的登录态（如小程序登录态、facebook登录等），但又希望能够同步该登录态到问卷系统的情况；（2）非标准接入MSDK，使用MSDK-V3或MSDK-V5无法正常采集openid的情况。

#### 接口说明

开发者通过动态拼接指定参数到问卷链接中，实现登录态传递和其他参数传递，并存储到问卷系统中，其中参数包括openid(必填）、source(可选）、info(可选)，分别存储到导出数据中的uid、uidSource、info列。

| 参数     | 是否必须 | 说明                 |
| ------ | ---- | ------------------ |
| openid | 是    | 登录用户的唯一ID          |
| source | 否    | 用户自定义渠道标识，例如wx/qq等 |
| info   | 否    | 额外的登录用户信息，可自定义     |

![3个参数内容会对应存储到导出数据的列中](<../.gitbook/assets/image (490).png>)

{% hint style="info" %}
**普通投放链接与内嵌投放链接示例对比**

【普通投放链接】

https://in.survey.imur.tencent.com/v2/?sid=5e8d767b76051f46707cf692

【内嵌投放链接】

&#x20;https://in.survey.imur.tencent.com/v2/?sid=5e8d767b76051f46707cf692\&openid=XXXX\&source=XXXX\&info=XXXX

_\*以上参数对应的值仅作展示使用_
{% endhint %}
