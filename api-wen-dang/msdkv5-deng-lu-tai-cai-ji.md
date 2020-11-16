# MSDK-V5登录态采集

对接了MSDK V5版本的APP，可在问卷设置中启用【MSDK登录验证】功能，选择版本为v5；用户提交问卷时，问卷系统会自动获取MSDK的登录态并存储在答题数据中。

![&#x914D;&#x7F6E;MSDK v5&#x767B;&#x5F55;&#x6001;&#x83B7;&#x53D6;&#x63A5;&#x5165;&#x6240;&#x9700;&#x8981;&#x7684;&#x53C2;&#x6570;](../.gitbook/assets/image%20%28358%29.png)

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



### 解密MSDK-V5登录态说明

API文档1参考：[https://docs.msdk.qq.com/v5/zh-CN/Server/](https://docs.msdk.qq.com/v5/zh-CN/Server/)

API文档2参考：[http://docs.msdk.qq.com/v5/zh-CN/Server/verify.html](http://docs.msdk.qq.com/v5/zh-CN/Server/verify.html)

（1）系统使用itopencodeparam参数进行登录态解密，此时要求必须带上os、gameid、channelid、ts、sig、source这6个参数参与，示例如下：

```text
https://hktest.itop.qq.com/v2/auth/decrypt?channelid=1&gameid=11&os=1&source=0&ts=1529907080&sig=8279b3214fc4900e7551ee21593b4d80&itopencodeparam=d9b48147c3b809a2bebbd8b2e96c26f1
```



### 登录失败提示

当系统无法获取正确的登录态时，会显示警告弹窗，主要导致失败的原因如下：

（1）itopencodeparam解密登录态时，由于缺失os、gameid、channelid、ts、sig、source等参数导致解密失败。

![](../.gitbook/assets/image%20%28293%29.png)



{% hint style="warning" %}
如MSDK-V5登录态采集接口联调失败，可改用参数传递（[严格校验模式](https://imur.gitbook.io/help_center/api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou)、[不校验模式](https://imur.gitbook.io/help_center/api-wen-dang/can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)）接口，实现登录态传递。
{% endhint %}

