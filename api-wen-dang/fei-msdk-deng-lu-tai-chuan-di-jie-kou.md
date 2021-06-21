# 参数传递接口（严格校验模式）

## 接口说明

### 接口定义

参数传递接口（严格校验模式）接口用于解决第三方开发者拥有自己系统的登录态（如小程序登录态、facebook登录等），但又希望能够同步该登录态到问卷系统的情况。

### 使用场景

以下几种情况可以**不需要**接入非MSDK登录态传递接口：

* 问卷内嵌到游戏中，问卷系统默认支持MSDK登录态处理，可在问卷编辑页选择【设置】-&gt; 【MSDK登录验证】打开该功能，当前仅支持v3和v5版本MSDK登录；
* 仅需要做每个用户答题限制，不关注采集的用户uid，可以选择使用微信或者手Q登录，可在问卷编辑页选择【设置】-&gt; 【微信、QQ登录验证】打开该功能；

### 交互流程

![](../.gitbook/assets/login_uml.jpg)

开发者仅需关注开发者服务器流程，重点关注签名以及登录重定向url的生成。

### sign签名算法

#### **算法流程**

1. 提供必要参数（详情看API接口，空值不需要参与签名），使用kv数据结构；
2. 添加appSecret作为签名密钥字段到kv数据结构；
3. 对key进行按ascii升序排序；
4. 遍历排序后的kv数据结构，把所有元素，按照“key1value1key2value2”的模式拼接成字符串；
5. 对拼接的数据库进行md5摘要，即可得sign签名；
6. 添加sign作为签名字段到kv数据结构；
7. 将kv数据结构转换成http的query请求参数；
8. 带上query请求参数调用登录态传递接口。

#### **代码示例**

_PHP代码_

```php
<?php
$appSecret = 'iamsecret';

$sid = '5dc5727a76051f14b96d5172';

$query = [
    'sid' => $sid,
    'uid' => 'user_id',
    'timestamp' => time(),
    'source' => 'dwk',
    'info' => 'extra_info',
    // 登录完成后系统会跳转到redirect的地址，一般使用的是问卷投放链接，会包括sid、lang内容
    // 如果有登录态回调参数，请参考【API文档】-> 【登录态回调接口】添加需要的参数
    // 注意：这里的域名要根据投放的域名做修改，详情看文档下方【API接口】
    'redirect' => 'https://in.survey.imur.tencent.com/index.html?sid='.$sid,
];

// 添加密钥
$params = array_merge($query, [
    'appSecret' => $appSecret,
]);

ksort($params);

$str = '';
foreach ($params as $key => $value) {
    // 值为空的参数不参与加密
    if ($value !== '') {
        $str .= $key.$value;
    }
}

$query['sign'] = strtolower(md5($str));

// 注意：这里的域名要根据投放的域名做修改，详情看文档下方【API接口】
$redirectUrl = 'https://in.weisurvey.com/v2/api/autologin?'.http_build_query($query);

// 重定向
header('Location: '.$redirectUrl);
```

_请求url示例_

```text
 https://in.weisurvey.com/autologin?sid=5dc5727a76051f14b96d5172&uid=user_id&timestamp=1573455797&source=dwk&info=extra_info&redirect=https%3A%2F%2Fin.survey.imur.tencent.com%2Findex.html%3Fsid%3D5dc5727a76051f14b96d5172&sign=2ac5ab8ce6a9b306e07dc2664fe7d175
```

{% hint style="info" %}
**普通投放链接与内嵌投放链接示例对比**

【普通投放链接】

https://in.survey.imur.tencent.com/?sid=5e8d767b76051f46707cf692&lang=zh-CHS&ADTAG=sid.5e8d767b76051f46707cf692

【内嵌投放链接】

 https://inapi.survey.imur.tencent.com/autologin?sid=5e8d767b76051f46707cf692&uid=user\_id&timestamp=1573455797&source=dwk&info=extra\_info&redirect=https%3A%2F%2Fin.survey.imur.tencent.com%2F%3Fsid%3D5e8d767b76051f46707cf692%26lang%3Dzh-CHS%26ADTAG%3Dsid.5e8d767b76051f46707cf692&sign=2ac5ab8ce6a9b306e07dc2664fe7d175

_\*以上参数对应的值仅作展示使用_
{% endhint %}

## **接口参数说明**

### **登录接口地址**

请根据业务投放域名与国内、海外选择接入接口。

#### **国内投放**

```text
国内投放拥有两套域名，分为tencent域与非tencent域，开发时需要注意

tencent域：
问卷投放域名为https://in.survey.imur.tencent.com/?sid=xxx则为tencent域，对应登录接口为：
https://in.survey.imur.tencent.com/v2/api/autologin?

非tencent域：
问卷投放域名为https://in.weisurvey.com/?sid=xxx则为非tencent域，对应登录接口为：
https://in.weisurvey.com/v2/api/autologin?
```

#### **海外投放**

```text
海外投放拥有三套域名，分为tencent域与非tencent域，开发时需要注意

tencent域：
问卷投放域名为https://out.survey.imur.tencent.com/?sid=xxx则为tencent域，对应登录接口为：
https://out.survey.imur.tencent.com/v2/api/autologin?

非tencent域：
问卷投放域名为https://out.weisurvey.com/?sid=xxx则为非tencent域，对应登录接口为：
https://out.weisurvey.com/v2/api/autologin?

！！新海外环境：
问卷投放域名为https://user.outweisurvey.com/?sid=xxxxx则为新海外环境，对应登录接口为：
https://user.outweisurvey.com/v2/api/autologin?
```

### **参数说明**

使用GET请求方式传参。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x53C2;&#x6570;</th>
      <th style="text-align:left">&#x662F;&#x5426;&#x5FC5;&#x987B;</th>
      <th style="text-align:left">&#x662F;&#x5426;&#x53C2;&#x4E0E;&#x52A0;&#x5BC6;</th>
      <th style="text-align:left">&#x6570;&#x636E;&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x9650;&#x5236;&#x957F;&#x5EA6;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">sid</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">32</td>
      <td style="text-align:left">&#x95EE;&#x5377;id&#xFF0C;&#x4ECE;&#x95EE;&#x5377;&#x94FE;&#x63A5;&#x53EF;&#x89E3;&#x6790;</td>
    </tr>
    <tr>
      <td style="text-align:left">uid</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">255</td>
      <td style="text-align:left">&#x767B;&#x5F55;&#x7528;&#x6237;&#x7684;&#x552F;&#x4E00;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">timestamp</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">int</td>
      <td style="text-align:left">10&#x4F4D;</td>
      <td style="text-align:left">&#x65F6;&#x95F4;&#x6233;</td>
    </tr>
    <tr>
      <td style="text-align:left">redirect</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">url&#x5730;&#x5740;</td>
      <td style="text-align:left">
        <p>&#x767B;&#x5F55;&#x6210;&#x529F;&#x4E4B;&#x540E;&#x8DF3;&#x8F6C;&#x7684;&#x9875;&#x9762;url&#xFF0C;&#x4E00;&#x822C;&#x4F7F;&#x7528;&#x7684;&#x662F;&#x95EE;&#x5377;&#x7684;&#x94FE;&#x63A5;</p>
        <p>&#x3010;&#x6CE8;&#x3011;</p>
        <ol>
          <li><b>&#x52A0;&#x5BC6;sign</b>&#x65F6;&#x4F7F;&#x7528;&#x539F;&#x59CB;URL&#xFF1B;<b>&#x62FC;&#x63A5;&#x4E3A;&#x5185;&#x5D4C;&#x6295;&#x653E;&#x94FE;&#x63A5;</b>&#x65F6;&#xFF0C;&#x9700;&#x5148;&#x628A;URL&#x8FDB;&#x884C;encode&#x540E;&#x8D4B;&#x503C;&#x5230;redirect&#xFF0C;&#x518D;&#x62FC;&#x5230;&#x5185;&#x5D4C;&#x6295;&#x653E;&#x94FE;&#x63A5;&#x4E2D;</li>
          <li>&#x56DE;&#x8C03;&#x4E2D;&#x7684;callback&#x3001;callback_params&#x9700;&#x5148;&#x6CE8;&#x5165;&#x5230;&#x95EE;&#x5377;&#x539F;&#x59CB;url&#xFF0C;&#x518D;&#x628A;&#x6B64;url&#x6309;&#x6B65;&#x9AA4;1&#x8D4B;&#x503C;&#x5230;redirect</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">source</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">2-10&#x4F4D;&#x82F1;&#x6587;</td>
      <td style="text-align:left">&#x7528;&#x6237;&#x81EA;&#x5B9A;&#x4E49;&#x6E20;&#x9053;&#x6807;&#x8BC6;</td>
    </tr>
    <tr>
      <td style="text-align:left">sign</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">32</td>
      <td style="text-align:left">&#x7B7E;&#x540D;&#xFF0C;&#x53C2;&#x8003;&#x7B7E;&#x540D;&#x7B97;&#x6CD5;</td>
    </tr>
    <tr>
      <td style="text-align:left">info</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">255</td>
      <td style="text-align:left">&#x989D;&#x5916;&#x7684;&#x767B;&#x5F55;&#x7528;&#x6237;&#x4FE1;&#x606F;&#xFF0C;&#x53EF;&#x81EA;&#x5B9A;&#x4E49;&#xFF1B;&#x4E3A;&#x7A7A;&#x65F6;&#x4E0D;&#x53C2;&#x4E0E;&#x52A0;&#x5BC6;</td>
    </tr>
  </tbody>
</table>

### 问卷设置

支持在问卷设置页面自定义密钥

![&#x914D;&#x7F6E;&#x5BC6;&#x94A5;](../.gitbook/assets/image%20%2818%29.png)

## 常见问题

