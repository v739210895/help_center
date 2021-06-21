# 登录态回调接口

## 接口说明

### 接口定义

用户提交问卷后，问卷系统将登录态等参数回调给开发者，适用于奖励发放、业务状态修改等场景。

#### 

### 使用场景

适用于开发者接入问卷系统后，需要用户在答题之后将用户等相关信息**回传给开发者服务端**的情况，注意这个回传动作是问卷服务端异步完成的，会有一定的时延（秒级）。

登录态回调接口的配置在问卷编辑下的【设置】-&gt;【登录态回调接口】开启，需要用户配置【密钥】与【回调地址】，并在【回调地址】对请求参数进行签名验证，防止恶意刷接口。

{% hint style="info" %}
支持公网回调和内网L5回调

1、回调地址以http://或者https://开头

2、支持L5地址，如：http://12345601:987654/surveytest1
{% endhint %}

### 

### sign签名算法

#### **算法流程**

1. 提供必要参数（详情看API接口），使用kv数据结构；
2. 添加appSecret作为签名密钥字段到kv数据结构；
3. 对key进行按ascii升序排序；
4. 遍历排序后的kv数据结构，把所有元素，按照“key1value1key2value2”的模式拼接成字符串；
5. 对拼接的数据库进行md5摘要，即可得sign签名；
6. 对比接收到的sign和5中计算得到的sign签名；
7. 返回状态码status。

{% hint style="info" %}
1. appSecret即回调密钥，和回调地址一样，在问卷的“设置”页配置。配置方法详见[登录态回调配置](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao.md#deng-lu-tai-hui-tiao-jie-kou)
2. 拼接后的加密字符串示例 appSecretuIVtlG06callback\_paramscallbackparamsinfotestinfosid5fe4428376051f85cc5f3973timestamp1609408137uidtestuseruid\_sourcetestsourceuser\_typeweak\_third\_party 【注】只有默认参数和appSecret参与计算签名，值为空的默认参数和其他未说明的参数不参与加密计算。
{% endhint %}



#### **代码示例**

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

## **回调参数说明**

### **参数说明**

回调调用开发者的接口是使用GET请求。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x53C2;&#x6570;</th>
      <th style="text-align:left">&#x662F;&#x5426;&#x5FC5;&#x4F20;</th>
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
      <td style="text-align:left">&#x95EE;&#x5377;id</td>
    </tr>
    <tr>
      <td style="text-align:left">uid</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">255</td>
      <td style="text-align:left">&#x4EC5;&#x5728;&#x95EE;&#x5377;&#x9700;&#x8981;&#x767B;&#x5F55;&#x65F6;&#x4F20;&#x9012;&#xFF0C;&#x767B;&#x5F55;&#x7528;&#x6237;&#x7684;&#x552F;&#x4E00;ID&#xFF08;&#x5373;&#xFF0C;MSDK&#x767B;&#x5F55;&#x9A8C;&#x8BC1;&#x4E2D;&#x7684;&#x73A9;&#x5BB6;openid/&#x4E25;&#x683C;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#x4E0B;&#x4F20;&#x5165;&#x7684;uid/&#x4E0D;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#x4E0B;&#x4F20;&#x5165;&#x7684;openid&#xFF09;</td>
    </tr>
    <tr>
      <td style="text-align:left">user_type</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">2-10</td>
      <td style="text-align:left">&#x4EC5;&#x5728;&#x95EE;&#x5377;&#x9700;&#x8981;&#x767B;&#x5F55;&#x65F6;&#x4F20;&#x9012;&#xFF0C;&#x767B;&#x5F55;&#x7528;&#x6237;&#x7C7B;&#x578B;&#xFF0C;&#x5305;&#x542B;&#xFF1A;wechat(&#x5FAE;&#x4FE1;)&#x3001;qq(QQ&#x767B;&#x5F55;)&#x3001;msdk(&#x6E38;&#x620F;&#x5185;)&#x3001;third_party(&#x53C2;&#x6570;&#x4F20;&#x9012;-&#x4E25;&#x683C;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;)&#x3001;weak_third_party&#xFF08;&#x53C2;&#x6570;&#x4F20;&#x9012;-&#x4E0D;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#xFF09;</td>
    </tr>
    <tr>
      <td style="text-align:left">uid_source</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">2-10</td>
      <td style="text-align:left">&#x4EC5;&#x5728;&#x95EE;&#x5377;&#x9700;&#x8981;&#x767B;&#x5F55;&#x65F6;&#x4F20;&#x9012;&#xFF0C;&#x767B;&#x5F55;&#x7528;&#x6237;&#x6765;&#x6E90;&#xFF0C;&#x5F53;&#x524D;&#x53EA;&#x5728;msdk&#x4E0B;&#x6709;&#x503C;wx&#x4E0E;qq&#xFF0C;&#x975E;MSDK&#x767B;&#x5F55;&#x6001;&#x4F20;&#x9012;&#x5219;&#x9700;&#x8981;&#x5F00;&#x53D1;&#x8005;&#x81EA;&#x5DF1;&#x5B9A;&#x4E49;</td>
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
      <td style="text-align:left">sign</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">32</td>
      <td style="text-align:left">&#x7B7E;&#x540D;&#xFF0C;&#x53C2;&#x8003;&#x7B7E;&#x540D;&#x7B97;&#x6CD5;</td>
    </tr>
    <tr>
      <td style="text-align:left">callback_params</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">255</td>
      <td style="text-align:left">
        <p>&#x5F00;&#x53D1;&#x8005;&#x81EA;&#x5B9A;&#x4E49;&#x56DE;&#x8C03;&#x53C2;&#x6570;&#xFF0C;&#x4E1A;&#x52A1;&#x9700;&#x8981;&#x989D;&#x5916;&#x7684;&#x53C2;&#x6570;&#x5219;&#x53EF;&#x4EE5;&#x4F7F;&#x7528;&#x3002;&#x3010;&#x6CE8;&#x3011;</p>
        <p>1.&#x8BE5;&#x53C2;&#x6570;&#x662F;&#x7531;&#x5F00;&#x53D1;&#x8005;&#x901A;&#x8FC7;&#x95EE;&#x5377;&#x94FE;&#x63A5;<b>&#x900F;&#x4F20;</b>&#x5230;&#x5F00;&#x53D1;&#x8005;&#x670D;&#x52A1;&#x7AEF;&#x7684;&#xFF0C;&#x4F8B;&#x5982;&#xFF1A;https://in.survey.imur.tencent.com/?sid=xxx&amp;</p>
        <p>lang=zh-CHS&amp;callback_params=xxxxx</p>
        <p>2.&#x5982;&#x900F;&#x4F20;&#x65F6;&#x503C;&#x88AB;encode&#xFF0C;&#x5219;&#x52A0;&#x5BC6;&#x65F6;&#x9700;&#x5148;decode</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">info</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">255</td>
      <td style="text-align:left">&#x767B;&#x5F55;&#x7528;&#x6237;&#x989D;&#x5916;&#x7684;&#x4FE1;&#x606F;&#x3002;&#x8BE5;&#x5B57;&#x6BB5;&#x9700;&#x914D;&#x5408;
        <a
        href="fei-msdk-deng-lu-tai-chuan-di-jie-kou.md">&#x53C2;&#x6570;&#x4F20;&#x9012;&#xFF08;&#x4E25;&#x683C;&#x6821;&#x9A8C;&#xFF09;</a>/
          <a
          href="can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi.md">&#x53C2;&#x6570;&#x4F20;&#x9012;&#xFF08;&#x4E0D;&#x6821;&#x9A8C;&#xFF09;</a>&#x4F7F;&#x7528;&#xFF1B;&#x5982;&#x4F7F;&#x7528;MSDK
            v3/v5&#x3001;INTL&#x81EA;&#x52A8;&#x767B;&#x5F55;&#xFF0C;info&#x4EC5;&#x4F5C;&#x4E3A;&#x666E;&#x901A;&#x53C2;&#x6570;&#x900F;&#x4F20;&#x3001;&#x4E0D;&#x53C2;&#x4E0E;&#x52A0;&#x5BC6;&#x3002;</td>
    </tr>
  </tbody>
</table>

{% hint style="info" %}
1. 非必传参数有值时参与加密，未传则不参与加密
2. 本文档未说明的参数不参与加密，可参考：[为什么会接收到文档中未说明的回调参数](../chang-jian-wen-ti/wei-shen-me-hui-jie-shou-dao-wen-dang-zhong-wei-shuo-ming-de-hui-tiao-can-shu.md)
3. 如使用MSDK v3/v5、INTL自动登录，info仅作为普通参数透传，不参与加密，也不采集到答案中。
{% endhint %}

### **回调成功约定返回格式**

开发者接收到回调并正常处理业务流程后，必需返回以下指定的json格式到问卷服务端：

```javascript
{
    "status": "ok"
}
```

### 回调业务码

如果业务方需要在回调中做一些特定标识，可以传递business\_code字段，问卷系统会存储该字段的值到es中，可以用来在开放接口中根据该标识筛选数据，business\_code值范围必须在 -32768 ~ 32767，如果超过该范围，则不会存储。示例：

```javascript
{
    "status": "ok",
    "business_code": 1000
}
```

{% hint style="info" %}
business\_code必须是int16类型，即 -32768 ~ 32767

回调业务码只会在status为ok的情况下写入
{% endhint %}

### 同一问卷支持设置多个回调地址

投放时**客户端**在问卷链接中注入callback参数，用以区分该次提交后回调到哪个回调地址中。最多可配置10个回调地址，具体回调到哪个实际由客户端指定。

**注：**每次提交问卷仅能回调到一个地址中，若问卷链接未注入callback参数，默认回调到地址1。

{% hint style="info" %}
如投放链接中注入callback的值为2，则提交后系统自动把登录态信息回调到回调地址2中

https://in.weisurvey.com/?sid=5f87b81376051f331039dfe5&openid={openid}**&callback=2**
{% endhint %}

![&#x591A;&#x4E2A;&#x56DE;&#x8C03;&#x5730;&#x5740;&#x914D;&#x7F6E;](../.gitbook/assets/image%20%28661%29.png)

## 回调接口调试工具

可使用回调接口调试工具（建议使用chrome打开）确认调通回调与签名验证。

\*\*\*\*[**https://test.a.imur.tencent.com/static/tools/index.html\#/callback**](https://test.a.imur.tencent.com/static/tools/index.html#/callback)\*\*\*\*

![&#x56DE;&#x8C03;&#x63A5;&#x53E3;&#x8C03;&#x8BD5;&#x5DE5;&#x5177;](../.gitbook/assets/image%20%28381%29.png)



## 常见问题

### [为什么收不到回调消息？](../chang-jian-wen-ti/wei-shen-me-shou-bu-dao-hui-tiao-xiao-xi.md)

### [为什么会接收到文档中未说明的回调参数？](../chang-jian-wen-ti/wei-shen-me-hui-jie-shou-dao-wen-dang-zhong-wei-shuo-ming-de-hui-tiao-can-shu.md)

