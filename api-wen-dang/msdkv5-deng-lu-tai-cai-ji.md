# MSDK-V5登录态采集

对接了MSDK V5版本的APP，可在问卷设置的登录验证中选择【MSDK v5】登录功能；用户提交问卷时，问卷系统会自动获取MSDK的登录态（如gopenid）并存储在答题数据中。

![配置MSDK v5自动登录所需要的参数](<../.gitbook/assets/image (28).png>)

## 参数配置说明

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



## MSDK-V5登录态加解密说明

问卷系统后台用于解密获取玩家登录态流程的说明，游戏侧仅需关注是否有在问卷链接后**注入正确的登录态参数**。

### 游戏客户端获取登录态加密票据

游戏客户端需通过MSDK webview自带接口在把问卷链接加密并注入登录态信息；参数包括：itopencodeparam、algorithm、channelid、encode、gameid、os、ts、version、seq、sig、source等。

```
//原始问卷链接
https://in.weisurvey.com/?sid=60ebdefe76051f6b8a37f782

//添加加密票据后的问卷链接
https://in.weisurvey.com/?sid=60ebdefe76051f6b8a37f782&algorithm=itop&encode=2&gameid=12&os=1&ts=1542889299&version=2.2.000.2607.2607&seq=11-5d0f17db-ef1e-44cd-88d7-57b556cc63ce-53&sig=eb6ee5ab9418d1c8e6400608815e76f2&itopencodeparam=F5382C12988BADA6F659B443ACE9978C14DE1B62EB1274AEFDECC219DE635C2B
```

#### 方式一：调用OpenUrl接口打开链接时，参数isUseURLEndode赋值为true

MSDK文档参考：

【打开网页OpenUrl】[http://doc.itop.woa.com/v5/zh-CN/Module/WebView.html#22-%E6%89%93%E5%BC%80%E7%BD%91%E9%A1%B5](http://doc.itop.woa.com/v5/zh-CN/Module/WebView.html#22-%E6%89%93%E5%BC%80%E7%BD%91%E9%A1%B5)

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>MSDK文档</p></figcaption></figure>

#### 方式二：调用（获取加密票据）接口在链接后注入登录态参数

MSDK文档参考：

【获取加密票据GetEncodeUrl】[http://doc.itop.woa.com/v5/zh-CN/Module/WebView.html#23-%E8%8E%B7%E5%8F%96%E5%8A%A0%E5%AF%86%E7%A5%A8%E6%8D%AE](http://doc.itop.woa.com/v5/zh-CN/Module/WebView.html#23-%E8%8E%B7%E5%8F%96%E5%8A%A0%E5%AF%86%E7%A5%A8%E6%8D%AE)



{% hint style="danger" %}
以上两种注入登录态方式任选其一，不可同时使用，否则会重复注入多次登录态参数导致问卷侧解密失败，无法访问问卷。（报错提示：登录失败请刷新）
{% endhint %}



### 问卷系统解密获取登录态信息

问卷系统通过“解密校验”接口获取itopencodeparam解密后的明文gopenid，**游戏侧无须关注**。

MSDK文档参考：【解密校验】[http://doc.itop.woa.com//v5/zh-CN/Server/verify.html#%E4%BA%8C%E3%80%81%E8%A7%A3%E5%AF%86%E6%A0%A1%E9%AA%8C](http://doc.itop.woa.com/v5/zh-CN/Server/verify.html#%E4%BA%8C%E3%80%81%E8%A7%A3%E5%AF%86%E6%A0%A1%E9%AA%8C)



## 登录失败提示

当系统无法获取正确的登录态时，问卷页面会显示警告弹窗，主要导致失败的原因如下：

（1）itopencodeparam解密登录态时，由于缺失os、gameid、channelid、ts、sig、source等参数导致解密失败。

（2）注入登录态参数后的问卷链接过长，部分参数被截断导致参数缺失。游戏客户端需自行处理。

（3）重复注入多次登录态参数导致解密失败。游戏客户端需排查OpenUrl()的isUseURLEncode是否为true，若是，则不需要另外调用GetEncodeUrl()。

![登录失败](<../.gitbook/assets/image (301).png>)

{% hint style="warning" %}
若MSDK-V5登录态采集接口联调失败，可改用参数传递（[严格校验模式](https://imur.gitbook.io/help\_center/api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou)、[不校验模式](https://imur.gitbook.io/help\_center/api-wen-dang/can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)）接口，实现登录态传递。
{% endhint %}
