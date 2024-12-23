# 参数传递接口（不校验模式）

### 接口说明

#### 接口定义

参数传递接口（不校验模式）接口用于解决（1）第三方开发者拥有自己系统的登录态（如小程序登录态、facebook登录等），但又希望能够同步该登录态到问卷系统的情况；（2）非标准接入MSDK，使用MSDK-V3或MSDK-V5无法正常采集openid的情况。

#### 接口说明

开发者通过动态拼接指定参数到问卷链接中，实现登录态传递和其他参数传递，并存储到问卷系统中，其中参数包括openid(必填）、channel(可选）、info(可选)，分别存储到导出数据中的用户ID、用户ID渠道、自定义内容列。

<table data-header-hidden><thead><tr><th>参数</th><th width="106.33333333333331">是否必须</th><th>说明</th></tr></thead><tbody><tr><td>参数</td><td>是否必须</td><td>说明</td></tr><tr><td>openid</td><td>是</td><td>登录用户的唯一ID</td></tr><tr><td>source</td><td>否</td><td>用户自定义渠道标识，例如wx/qq等（仅在回调参数中返回，如需记录到答案，请使用channel）</td></tr><tr><td>channel</td><td>否</td><td>用户自定义渠道，例如wx/qq等，记录到答题数据中</td></tr><tr><td>info</td><td>否</td><td>额外的登录用户信息，可自定义。info值会记录到答题数据中的“自定义内容”字段。</td></tr><tr><td>callback_params</td><td>否</td><td>开发者自定义回调参数，业务需要额外的参数则可以使用</td></tr></tbody></table>



{% hint style="danger" %}
1. 各参数的赋值请勿带分号;  斜杠/  百分号% ，支持数字、字母、下划线\_，横杠- 组合的字符串
2. info和partition均为“自定义内容”，请勿同时传入info和partition，否则其中一个参数的值会丢失。
{% endhint %}

![openid、channel、info会对应存储到导出数据的用户ID、渠道、自定义内容列](<../.gitbook/assets/image (713).png>)

{% hint style="info" %}
**普通投放链接与内嵌投放链接示例对比**

【普通投放链接】

[https://in.weisurvey.com](https://in.weisurvey.com)/v2/?sid=5e8d767b76051f46707cf692

【内嵌投放链接】

&#x20;[https://in.weisurvey.com](https://in.weisurvey.com)/v2/?sid=5e8d767b76051f46707cf692\&openid=XXXX\&channel=XXXX\&info=XXXX

_\*以上参数对应的值仅作展示使用_
{% endhint %}
