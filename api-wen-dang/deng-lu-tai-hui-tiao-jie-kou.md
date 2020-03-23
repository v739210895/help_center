# 登录态回调接口

### [回调参数说明](deng-lu-tai-hui-tiao-jie-kou.md#sign-qian-ming-suan-fa)

### [常见问题](deng-lu-tai-hui-tiao-jie-kou.md#chang-jian-wen-ti-1)

### 接口说明

#### 接口定义

用户登录后，问卷系统将登录态等参数回调给开发者，适用于奖励发放、业务状态修改等场景。

#### 使用场景

适用于开发者接入问卷系统后，需要用户在答题之后将用户等相关信息回传给开发者服务端的情况，注意这个回传动作是问卷服务端异步完成的，会有一定的时延（秒级）。

登录态回调接口的配置在问卷编辑下的【设置】-&gt;【登录态回调接口】开启，需要用户配置【密钥】与【回调地址】，并在【回调地址】对请求参数进行签名验证，防止恶意刷接口。

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

**回调参数说明**

**参数说明**

回调调用开发者的接口是使用GET请求。

| 参数 | 是否必传 | 数据类型 | 限制长度 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| sid | 是 | string | 32 | 问卷id |
| uid | 否 | string | 255 | 仅在问卷需要登录时传递，登录用户的唯一ID |
| user\_type | 否 | string | 2-10 | 仅在问卷需要登录时传递，登录用户类型，包含：wechat\(微信\)、qq\(QQ登录\)、msdk\(游戏内\)、third\_party\(非MSDK登录态传递\) |
| uid\_source | 否 | string | 2-10 | 仅在问卷需要登录时传递，登录用户来源，当前只在msdk下有值wx与qq，非MSDK登录态传递则需要开发者自己定义 |
| timestamp | 是 | int | 10位 | 时间戳 |
| sign | 是 | string | 32 | 签名，参考签名算法 |
| callback\_params | 否 | string | 255 | 开发者自定义回调参数，业务需要额外的参数则可以使用。注意：该参数是由开发者通过问卷链接**透传**到开发者服务端的，例如：https://in.survey.imur.tencent.com/index.html?sid=xxxx&callback\_params=xxxxx。 |
| info | 否 | string | 255 | 登录用户额外的信息，该字段可以配合[非MSDK登录态传递接口使用](fei-msdk-deng-lu-tai-chuan-di-jie-kou.md)。 |

**回调成功约定返回格式**

开发者接收到回调并正常处理业务流程后，必需返回以下指定的json格式到问卷服务端：

```javascript
{
    "status": "ok"
}
```

#### 常见问题

