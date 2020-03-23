# 非MSDK-V3登录态传递接口

### [常见问题](fei-msdk-deng-lu-tai-chuan-di-jie-kou.md#chang-jian-wen-ti-1)

### 接口说明

#### 接口定义

非MSDK登录态传递接口用于解决第三方开发者拥有自己系统的登录态（如小程序登录态、facebook登录等），但又希望能够同步该登录态到问卷系统的情况。

#### 使用场景

以下几种情况可以**不需要**接入非MSDK-V3登录态传递接口：

* 问卷内嵌到游戏中，问卷系统默认支持MSDK登录态处理，可在问卷编辑页选择【设置】-&gt; 【MSDK登录验证】打开该功能，当前仅支持v3版本MSDK登录；
* 仅需要做每个用户答题限制，不关注采集的用户uid，可以选择使用微信或者手Q登录，可在问卷编辑页选择【设置】-&gt; 【微信、QQ登录验证】打开该功能；

#### 交互流程

![](../.gitbook/assets/login_uml.jpg)

开发者仅需关注开发者服务器流程，重点关注签名以及登录重定向url的生成。

#### sign签名算法

**算法流程**

1. 提供必要参数（详情看API接口），使用kv数据结构；
2. 添加appSecret作为签名密钥字段到kv数据结构；
3. 对key进行按ascii升序排序；
4. 遍历排序后的kv数据结构，把所有元素，按照“key1value1key2value2”的模式拼接成字符串；
5. 对拼接的数据库进行md5摘要，即可得sign签名；
6. 添加sign作为签名字段到kv数据结构；
7. 将kv数据结构转换成http的query请求参数；
8. 带上query请求参数调用登录态传递接口。

**代码示例**

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
    'redirect' => 'https://in.survey.imur.tencent.com/index.html?sid='.$sid,
];

// 添加密钥
$params = array_merge($query, [
    'appSecret' => $appSecret,
]);

ksort($params);

$str = '';
foreach ($params as $key => $value) {
    $str .= $key.$value;
}

$query['sign'] = strtolower(md5($str));

$redirectUrl = 'https://inapi.survey.imur.tencent.com/autologin?'.http_build_query($query);

// 重定向
header('Location: '.$redirectUrl);
```

_请求url示例_

```text
 https://inapi.survey.imur.tencent.com/autologin?sid=5dc5727a76051f14b96d5172&uid=user_id&timestamp=1573455797&source=dwk&info=extra_info&redirect=https%3A%2F%2Fin.survey.imur.tencent.com%2Findex.html%3Fsid%3D5dc5727a76051f14b96d5172&sign=2ac5ab8ce6a9b306e07dc2664fe7d175
```

**API接口**

**接口地址**

```text
测试环境：
https://test.inapi.survey.imur.tencent.com/autologin?

正式环境：
https://inapi.survey.imur.tencent.com/autologin?
https://inapi.weisurvey.com/autologin?
```

**参数说明**

使用GET请求方式传参。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x53C2;&#x6570;</th>
      <th style="text-align:left">&#x662F;&#x5426;&#x5FC5;&#x987B;</th>
      <th style="text-align:left">&#x6570;&#x636E;&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x9650;&#x5236;&#x957F;&#x5EA6;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">uid</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">255</td>
      <td style="text-align:left">&#x767B;&#x5F55;&#x7528;&#x6237;&#x7684;&#x552F;&#x4E00;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">timestamp</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">int</td>
      <td style="text-align:left">10&#x4F4D;</td>
      <td style="text-align:left">&#x65F6;&#x95F4;&#x6233;</td>
    </tr>
    <tr>
      <td style="text-align:left">redirect</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">url&#x5730;&#x5740;</td>
      <td style="text-align:left">&#x767B;&#x5F55;&#x6210;&#x529F;&#x4E4B;&#x540E;&#x8DF3;&#x8F6C;&#x7684;&#x9875;&#x9762;url&#xFF0C;&#x4E00;&#x822C;&#x4F7F;&#x7528;&#x7684;&#x662F;&#x95EE;&#x5377;&#x7684;&#x94FE;&#x63A5;</td>
    </tr>
    <tr>
      <td style="text-align:left">source</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">2-10&#x4F4D;&#x82F1;&#x6587;</td>
      <td style="text-align:left">&#x7528;&#x6237;&#x81EA;&#x5B9A;&#x4E49;&#x6E20;&#x9053;&#x6807;&#x8BC6;</td>
    </tr>
    <tr>
      <td style="text-align:left">sign</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">32</td>
      <td style="text-align:left">&#x7B7E;&#x540D;&#xFF0C;&#x53C2;&#x8003;&#x7B7E;&#x540D;&#x7B97;&#x6CD5;</td>
    </tr>
    <tr>
      <td style="text-align:left">callback_params</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">255</td>
      <td style="text-align:left">
        <p>&#x5F00;&#x53D1;&#x8005;&#x81EA;&#x5B9A;&#x4E49;&#x56DE;&#x8C03;&#x53C2;&#x6570;&#xFF0C;&#x4E1A;&#x52A1;&#x9700;&#x8981;&#x989D;&#x5916;&#x7684;&#x53C2;&#x6570;&#x5219;&#x53EF;&#x4EE5;&#x4F7F;&#x7528;&#x3002;&#x6CE8;&#x610F;&#xFF1A;&#x8BE5;&#x53C2;&#x6570;&#x662F;&#x7531;&#x5F00;&#x53D1;&#x8005;&#x901A;&#x8FC7;&#x95EE;&#x5377;&#x94FE;&#x63A5;<b>&#x900F;&#x4F20;</b>&#x5230;&#x5F00;&#x53D1;&#x8005;&#x670D;&#x52A1;&#x7AEF;&#x7684;&#xFF0C;&#x914D;&#x5408;
          <a
          href="https://imur.gitbook.io/help_center/api-wen-dang/deng-lu-tai-hui-tiao-jie-kou">&#x767B;&#x5F55;&#x6001;&#x56DE;&#x8C03;&#x63A5;&#x53E3;&#x4F7F;&#x7528;</a>&#x3002;&#x4F8B;&#x5982;&#xFF1A;https://in.survey.imur.tencent.com/?sid=xxx&amp;</p>
        <p>lang=zh-CHS&amp;callback_params=xxxxx</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">info</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">255</td>
      <td style="text-align:left">&#x989D;&#x5916;&#x7684;&#x767B;&#x5F55;&#x7528;&#x6237;&#x4FE1;&#x606F;&#xFF0C;&#x53EF;&#x81EA;&#x5B9A;&#x4E49;</td>
    </tr>
  </tbody>
</table>#### 常见问题

