# 登录态回调接口

### [回调参数说明](deng-lu-tai-hui-tiao-jie-kou.md#hui-tiao-can-shu-shuo-ming-1)

### [回调调试工具](deng-lu-tai-hui-tiao-jie-kou.md#hui-tiao-jie-kou-tiao-shi-gong-ju)

### [常见问题](deng-lu-tai-hui-tiao-jie-kou.md#chang-jian-wen-ti-1)

### 接口说明

#### 接口定义

用户登录后，问卷系统将登录态等参数回调给开发者，适用于奖励发放、业务状态修改等场景。

#### 

#### 使用场景

适用于开发者接入问卷系统后，需要用户在答题之后将用户等相关信息回传给开发者服务端的情况，注意这个回传动作是问卷服务端异步完成的，会有一定的时延（秒级）。

登录态回调接口的配置在问卷编辑下的【设置】-&gt;【登录态回调接口】开启，需要用户配置【密钥】与【回调地址】，并在【回调地址】对请求参数进行签名验证，防止恶意刷接口。

{% hint style="info" %}
支持公网回调和内网L5回调

1、回调地址以http://或者https://开头

2、支持L5地址，如：http://12345601:987654/survey
{% endhint %}

### 

#### sign签名算法

**算法流程**

1. 提供必要参数（详情看API接口），使用kv数据结构；
2. 添加appSecret作为签名密钥字段到kv数据结构；
3. 对key进行按ascii升序排序；
4. 遍历排序后的kv数据结构，把所有元素，按照“key1value1key2value2”的模式拼接成字符串；
5. 对拼接的数据库进行md5摘要，即可得sign签名；
6. 对比接收到的sign和5中计算得到的sign签名；
7. 返回状态码status。

**代码示例**

_PHP代码_ 

```php
<?php
$query = $_GET;

$appSecret = 'iamsecret';

$sign = $query['sign'];
unset($query['sign']);

// 添加密钥
$params = array_merge($query, [
    'appSecret' => $appSecret,
]);

ksort($params);

$str = '';
foreach ($params as $key => $value) {
    $str .= $key.$value;
}

$mySign = strtolower(md5($str));

echo json_encode([
    'status' => ($mySign === $sign) ? 'ok' : 'failed',
]);
```

_回调URL示例_

```aspnet
开发者回调接口url?sid=5da414769e8aa80019305e32&timestamp=1573556685&uid=test_user&user_type=third_party&uid_source=qq&info=afdadsfasdfasdf&callback_params=callbackparams&sign=38408d6222e1a4c6fa598e4820443ca8
```

#### \*\*\*\*

#### **回调参数说明**

**参数说明**

回调调用开发者的接口是使用GET请求。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x53C2;&#x6570;</th>
      <th style="text-align:left">&#x662F;&#x5426;&#x5FC5;&#x4F20;</th>
      <th style="text-align:left">&#x6570;&#x636E;&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x9650;&#x5236;&#x957F;&#x5EA6;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">sid</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">32</td>
      <td style="text-align:left">&#x95EE;&#x5377;id</td>
    </tr>
    <tr>
      <td style="text-align:left">uid</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">255</td>
      <td style="text-align:left">&#x4EC5;&#x5728;&#x95EE;&#x5377;&#x9700;&#x8981;&#x767B;&#x5F55;&#x65F6;&#x4F20;&#x9012;&#xFF0C;&#x767B;&#x5F55;&#x7528;&#x6237;&#x7684;&#x552F;&#x4E00;ID&#xFF08;&#x5373;&#xFF0C;MSDK&#x767B;&#x5F55;&#x9A8C;&#x8BC1;&#x4E2D;&#x7684;&#x73A9;&#x5BB6;openid/&#x4E25;&#x683C;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#x4E0B;&#x4F20;&#x5165;&#x7684;uid/&#x4E0D;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#x4E0B;&#x4F20;&#x5165;&#x7684;openid&#xFF09;</td>
    </tr>
    <tr>
      <td style="text-align:left">user_type</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">2-10</td>
      <td style="text-align:left">&#x4EC5;&#x5728;&#x95EE;&#x5377;&#x9700;&#x8981;&#x767B;&#x5F55;&#x65F6;&#x4F20;&#x9012;&#xFF0C;&#x767B;&#x5F55;&#x7528;&#x6237;&#x7C7B;&#x578B;&#xFF0C;&#x5305;&#x542B;&#xFF1A;wechat(&#x5FAE;&#x4FE1;)&#x3001;qq(QQ&#x767B;&#x5F55;)&#x3001;msdk(&#x6E38;&#x620F;&#x5185;)&#x3001;third_party(&#x53C2;&#x6570;&#x4F20;&#x9012;-&#x4E25;&#x683C;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;)&#x3001;weak_third_party&#xFF08;&#x53C2;&#x6570;&#x4F20;&#x9012;-&#x4E0D;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#xFF09;</td>
    </tr>
    <tr>
      <td style="text-align:left">uid_source</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">2-10</td>
      <td style="text-align:left">&#x4EC5;&#x5728;&#x95EE;&#x5377;&#x9700;&#x8981;&#x767B;&#x5F55;&#x65F6;&#x4F20;&#x9012;&#xFF0C;&#x767B;&#x5F55;&#x7528;&#x6237;&#x6765;&#x6E90;&#xFF0C;&#x5F53;&#x524D;&#x53EA;&#x5728;msdk&#x4E0B;&#x6709;&#x503C;wx&#x4E0E;qq&#xFF0C;&#x975E;MSDK&#x767B;&#x5F55;&#x6001;&#x4F20;&#x9012;&#x5219;&#x9700;&#x8981;&#x5F00;&#x53D1;&#x8005;&#x81EA;&#x5DF1;&#x5B9A;&#x4E49;</td>
    </tr>
    <tr>
      <td style="text-align:left">timestamp</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">int</td>
      <td style="text-align:left">10&#x4F4D;</td>
      <td style="text-align:left">&#x65F6;&#x95F4;&#x6233;</td>
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
        <p>&#x5F00;&#x53D1;&#x8005;&#x81EA;&#x5B9A;&#x4E49;&#x56DE;&#x8C03;&#x53C2;&#x6570;&#xFF0C;&#x4E1A;&#x52A1;&#x9700;&#x8981;&#x989D;&#x5916;&#x7684;&#x53C2;&#x6570;&#x5219;&#x53EF;&#x4EE5;&#x4F7F;&#x7528;&#x3002;&#x6CE8;&#x610F;&#xFF1A;&#x8BE5;&#x53C2;&#x6570;&#x662F;&#x7531;&#x5F00;&#x53D1;&#x8005;&#x901A;&#x8FC7;&#x95EE;&#x5377;&#x94FE;&#x63A5;<b>&#x900F;&#x4F20;</b>&#x5230;&#x5F00;&#x53D1;&#x8005;&#x670D;&#x52A1;&#x7AEF;&#x7684;&#xFF0C;&#x4F8B;&#x5982;&#xFF1A;https://in.survey.imur.tencent.com/?sid=xxx&amp;</p>
        <p>lang=zh-CHS&amp;callback_params=xxxxx</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">info</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">255</td>
      <td style="text-align:left">&#x767B;&#x5F55;&#x7528;&#x6237;&#x989D;&#x5916;&#x7684;&#x4FE1;&#x606F;&#xFF0C;&#x8BE5;&#x5B57;&#x6BB5;&#x53EF;&#x4EE5;&#x914D;&#x5408;
        <a
        href="fei-msdk-deng-lu-tai-chuan-di-jie-kou.md">&#x975E;MSDK&#x767B;&#x5F55;&#x6001;&#x4F20;&#x9012;&#x63A5;&#x53E3;&#x4F7F;&#x7528;</a>&#x3002;</td>
    </tr>
  </tbody>
</table>

**回调成功约定返回格式**

开发者接收到回调并正常处理业务流程后，必需返回以下指定的json格式到问卷服务端：

```javascript
{
    "status": "ok"
}
```

#### 

#### 回调接口调试工具

可使用回调接口调试工具（建议使用chrome打开）确认调通回调与签名验证。

\*\*\*\*[**https://test.a.imur.tencent.com/static/tools/index.html\#/callback**](https://test.a.imur.tencent.com/static/tools/index.html#/callback)\*\*\*\*

![&#x56DE;&#x8C03;&#x63A5;&#x53E3;&#x8C03;&#x8BD5;&#x5DE5;&#x5177;](../.gitbook/assets/image%20%28381%29.png)

#### 常见问题

