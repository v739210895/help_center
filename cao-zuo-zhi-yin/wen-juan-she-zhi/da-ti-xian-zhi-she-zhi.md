# 答题限制设置

问卷系统支持采集不同类型的登录态，问卷设计者可参考以下流程，开启对应的功能。部分功能需要由开发者对接系统接口实现。

![](../../.gitbook/assets/image%20%2814%29.png)

![&#x7B54;&#x9898;&#x9650;&#x5236;&#x8BBE;&#x7F6E;](../../.gitbook/assets/image%20%28202%29.png)

## 微信、QQ登录验证

功能启用后，非MSDK内嵌投放时，问卷系统会自动拉起QQ/微信登录， 用户登录后才允许答题。此处会采集问卷系统用户的uid，在答题数据中记录并显示。

## MSDK登录验证

功能启用后，对于接入了msdk [v3](https://imur.gitbook.io/help_center/api-wen-dang/msdkv3-deng-lu-tai-cai-ji)或[v5](https://imur.gitbook.io/help_center/api-wen-dang/msdkv5-deng-lu-tai-cai-ji)的APP，问卷内嵌投放时，问卷系统会采集用户的openid，将openid解析并存储在uid列，在答题数据中显示。

{% hint style="info" %}
配置msdk v5登录态获取的参数中，“密钥”请填写飞鹰系统参数中的MSDK\_SERVER\_KEY
{% endhint %}

## 每个账号只能回答一次

此功能需要配合微信、QQ登录验证或MSDK登录验证使用，功能启用后，若该用户已回答过问卷，会禁止用户二次回答。

![&#x91CD;&#x590D;&#x7B54;&#x9898;&#x63D0;&#x793A;](../../.gitbook/assets/image%20%28390%29.png)

## 每个IP只能答一次

{% hint style="danger" %}
功能暂未开放使用
{% endhint %}

功能启用后，打开问卷时会根据用户IP进行校验，若该用户已回答过问卷，会禁止用户二次回答。

## 每个浏览器只能答一次

功能启用后，打开问卷时会根据用户的浏览器进行校验，若该用户已回答过问卷，会禁止用户二次回答。

{% hint style="info" %}
若用户清理浏览器缓存后，可再次回答问卷。
{% endhint %}

## 白名单答题限制

{% hint style="danger" %}
功能暂未开放使用
{% endhint %}

功能启用后，打开问卷时会先校验当前答题者是否白名单用户，白名单用户才能访问问卷。

### 白名单文件规则说明

#### QQ号/手机号

直接写入白名单用户的QQ号/手机号，每行一个号码。

#### openid

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x767B;&#x5F55;&#x9A8C;&#x8BC1;&#x65B9;&#x5F0F;</th>
      <th style="text-align:left">openid&#x503C;&#x8BF4;&#x660E;</th>
      <th style="text-align:left">&#x793A;&#x4F8B;&#x503C;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x5FAE;&#x4FE1;&#x3001;QQ&#x767B;&#x5F55;&#x9A8C;&#x8BC1;</td>
      <td style="text-align:left">
        <p>&#x7528;&#x6237;&#x901A;&#x8FC7;&#x5FAE;&#x4FE1;/QQ&#x767B;&#x5F55;&#x95EE;&#x5377;&#x540E;&#x7684;openid&#xFF08;&#x975E;&#x6E38;&#x620F;openid&#xFF09;&#xFF0C;</p>
        <p>QQ&#x53F7;&#x8F6C;openid&#x8BF7;&#x53C2;&#x8003;<a href="https://imur.gitbook.io/help_center/chang-jian-wen-ti/uidopenid-zhuan-huan-qq-hao#fu-lu-openid-shi-shen-me-ying-yong-nei-yong-hu-shen-fen-de-wei-yi-biao-shi">QQ&#x53F7;&#x8F6C;openid</a>
        </p>
      </td>
      <td style="text-align:left">
        <p>78F2938728791F866806043CEFF5222D</p>
        <p>oY2--whSvI7JPzmQWcRg7o60TpdQ</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MSDK&#x767B;&#x5F55;&#x9A8C;&#x8BC1;&#xFF1A;v3</td>
      <td style="text-align:left">&#x6E38;&#x620F;&#x5185;&#x7684;&#x73A9;&#x5BB6;openid</td>
      <td style="text-align:left">56C589029A4C0BD2282D5CD2DD5725F2</td>
    </tr>
    <tr>
      <td style="text-align:left">MSDK&#x767B;&#x5F55;&#x9A8C;&#x8BC1;&#xFF1A;v5</td>
      <td style="text-align:left">&#x6E38;&#x620F;&#x5185;&#x7684;&#x73A9;&#x5BB6;gopenid</td>
      <td style="text-align:left">13293484783071200846</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x53C2;&#x6570;&#x4F20;&#x9012;&#xFF08;&#x4E25;&#x683C;&#x6821;&#x9A8C;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>&#x53C2;&#x6570;&#x4F20;&#x9012;&#x65F6;&#x7684;uid&#x503C;&#xFF08;&#x7531;&#x6E38;&#x620F;&#x81EA;&#x5B9A;&#x4E49;&#xFF09;&#xFF0C;</p>
        <p>&#x8BE6;&#x60C5;&#x53EF;&#x53C2;&#x8003;<a href="../../api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou.md">&#x53C2;&#x6570;&#x4F20;&#x9012;&#x63A5;&#x53E3;&#xFF08;&#x4E25;&#x683C;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#xFF09;</a>
        </p>
        </td>
        <td style="text-align:left">30291658356950347</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x53C2;&#x6570;&#x4F20;&#x9012;&#xFF08;&#x4E0D;&#x6821;&#x9A8C;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>&#x53C2;&#x6570;&#x4F20;&#x9012;&#x65F6;&#x7684;openid&#x503C;&#xFF08;&#x7531;&#x6E38;&#x620F;&#x81EA;&#x5B9A;&#x4E49;&#xFF09;&#xFF0C;</p>
        <p>&#x8BE6;&#x60C5;&#x53EF;&#x53C2;&#x8003;<a href="../../api-wen-dang/can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi.md">&#x53C2;&#x6570;&#x4F20;&#x9012;&#x63A5;&#x53E3;&#xFF08;&#x4E0D;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#xFF09;</a>
        </p>
        </td>
        <td style="text-align:left">30291658356950347</td>
    </tr>
  </tbody>
</table>

