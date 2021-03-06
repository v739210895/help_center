# 答题限制设置

![&#x7B54;&#x9898;&#x9650;&#x5236;&#x8BBE;&#x7F6E;](../../../.gitbook/assets/image%20%28664%29.png)

## 每个用户ID只能回答一次

此功能需要配合微信、QQ登录验证或MSDK登录验证使用。功能启用后，根据用户ID判断该用户是否已答题，若已答题，不可打开问卷。重复答题提示语按所设置的答卷语言显示翻译。

![&#x91CD;&#x590D;&#x7B54;&#x9898;&#x63D0;&#x793A;](../../../.gitbook/assets/image%20%28667%29.png)

## 每个IP只能答一次

{% hint style="danger" %}
功能暂未开放使用
{% endhint %}

功能启用后，打开问卷时会根据用户IP进行校验，若该用户已回答过问卷，会禁止用户二次回答。

## 每个浏览器只能答一次

功能启用后，根据用户当前的浏览器标识判断该用户是否已答题，若该用户已答题，会禁止打开问卷。

{% hint style="info" %}
若用户清理浏览器缓存后，可再次回答问卷。
{% endhint %}

## 白名单答题限制

功能启用后，打开问卷时会先校验当前答题者是否白名单用户，白名单用户才能访问问卷。

![&#x767D;&#x540D;&#x5355;&#x8EAB;&#x4EFD;&#x9A8C;&#x8BC1;](../../../.gitbook/assets/image%20%28665%29.png)

{% hint style="info" %}
白名单文件大小限制**10MB**；白名单用户数量不限，可参考：

【openid】（22位）：可上传约30万个

【QQ号】（9位）：可上传约75万个

【手机号】（11位）：可上传约60万个
{% endhint %}

### 白名单文件规则说明

#### QQ号/手机号

直接写入白名单用户的QQ号/手机号，每行一个号码。

#### openid

直接写入白名单用户的openid，每行一个号码，需配合以下任一登录功能使用。

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
      <td style="text-align:left">&#x7528;&#x6237;&#x901A;&#x8FC7;&#x5FAE;&#x4FE1;/QQ&#x767B;&#x5F55;&#x95EE;&#x5377;&#x540E;&#x7684;openid&#xFF08;&#x975E;&#x6E38;&#x620F;openid&#xFF09;&#xFF0C;QQ&#x53F7;&#x8F6C;openid&#x65B9;&#x6CD5;&#x8BF7;&#x53C2;&#x8003;
        <a
        href="https://imur.gitbook.io/help_center/chang-jian-wen-ti/uidopenid-zhuan-huan-qq-hao#fu-lu-openid-shi-shen-me-ying-yong-nei-yong-hu-shen-fen-de-wei-yi-biao-shi">QQ&#x53F7;&#x8F6C;openid</a>
      </td>
      <td style="text-align:left">
        <p>&#x3010;QQ&#x3011;78F2938728791F866806043CEFF5222D</p>
        <p>&#x3010;&#x5FAE;&#x4FE1;&#x3011;</p>
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
        <p>&#x8BE6;&#x60C5;&#x53EF;&#x53C2;&#x8003;<a href="../../../api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou.md">&#x53C2;&#x6570;&#x4F20;&#x9012;&#x63A5;&#x53E3;&#xFF08;&#x4E25;&#x683C;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#xFF09;</a>
        </p>
        </td>
        <td style="text-align:left">30291658356950347</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x53C2;&#x6570;&#x4F20;&#x9012;&#xFF08;&#x4E0D;&#x6821;&#x9A8C;&#xFF09;</td>
      <td
      style="text-align:left">&#x53C2;&#x6570;&#x4F20;&#x9012;&#x65F6;&#x7684;openid&#x503C;&#xFF08;&#x7531;&#x6E38;&#x620F;&#x81EA;&#x5B9A;&#x4E49;&#xFF09;&#xFF0C;&#x8BE6;&#x60C5;&#x53EF;&#x53C2;&#x8003;
        <a
        href="../../../api-wen-dang/can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi.md">&#x53C2;&#x6570;&#x4F20;&#x9012;&#x63A5;&#x53E3;&#xFF08;&#x4E0D;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#xFF09;</a>
          </td>
          <td style="text-align:left">30291658356950347</td>
    </tr>
  </tbody>
</table>



