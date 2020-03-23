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

| 参数 | 是否必须 | 数据类型 | 限制长度 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| uid | 是 | string | 255 | 登录用户的唯一ID |
| timestamp | 是 | int | 10位 | 时间戳 |
| redirect | 是 | string | url地址 | 登录成功之后跳转的页面url，一般使用的是问卷的链接 |
| source | 是 | string | 2-10位英文 | 用户自定义渠道标识 |
| sign | 是 | string | 32 | 签名，参考签名算法 |
| callback\_params | 否 | string | 255 | 开发者自定义回调参数，业务需要额外的参数则可以使用。注意：该参数是由开发者通过问卷链接**透传**到开发者服务端的，配合登录态回调接口使用。例如：https://in.survey.imur.tencent.com/index.html?sid=xxxx&callback\_params=xxxxx。 |
| info | 否 | string | 255 | 额外的登录用户信息，可自定义 |

#### 常见问题

