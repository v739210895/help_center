# 传参/跳转/回调

问卷系统支持内嵌投放及参数传递、答题后跳转、参数回调等功能，用户可根据实际需要按以下各项设置。

![](../../.gitbook/assets/image%20%28561%29.png)

## 参数传递接口（严格校验模式）

对于未接入msdk的APP，问卷内嵌投放时，问卷系统通过开发者传递登录态的方式来采集用户的uid。功能开启后，弹窗显示密钥，密钥用于生成签名（密钥可自行修改或重新生成），点击确认关闭弹窗。

![&#x914D;&#x7F6E;&#x5BC6;&#x94A5;](../../.gitbook/assets/image%20%2818%29.png)

{% hint style="info" %}
【内嵌投放链接示例】 

https://inapi.survey.imur.tencent.com/autologin?sid=5e8d767b76051f46707cf692&uid=user\_id&timestamp=1573455797&source=dwk&info=extra\_info&redirect=https%3A%2F%2Fin.survey.imur.tencent.com%2F%3Fsid%5e8d767b76051f46707cf692%26lang%3Dzh-CHS%26ADTAG%3Dsid.5e8d767b76051f46707cf692&sign=2ac5ab8ce6a9b306e07dc2664fe7d175
{% endhint %}

点击“[参数传递接口（严格校验）](../../api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou.md)”查看API文档，了解内嵌投放链接的改造方法。

## 参数传递接口（不校验模式）

对于未接入msdk的APP，问卷内嵌投放时，问卷系统通过开发者传递登录态的方式来采集用户的uid。不校验模式开启功能后，只需在问卷链接后直接拼接参数即可把玩家信息等参数传递到问卷系统。

{% hint style="warning" %}
1. 不校验模式不进行签名校验，可能会存在被刷风险
2. 已开启不校验模式的问卷，若未正确拼接openid参数将无法打开问卷
{% endhint %}

![&#x53C2;&#x6570;&#x4F20;&#x9012;&#x63A5;&#x53E3;&#xFF08;&#x4E0D;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#xFF09;](../../.gitbook/assets/image%20%28570%29.png)

{% hint style="info" %}
**【内嵌投放链接】** 

https://in.survey.imur.tencent.com/?sid=5e8d767b76051f46707cf692&lang=zh-CHS&ADTAG=sid.5e8d767b76051f46707cf692&openid=XXXX&source=XXXX&info=XXXX
{% endhint %}

点击“[参数传递接口（不校验模式）](../../api-wen-dang/can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi.md)”查看API文档，了解问卷链接的改造方法。

## 提交问卷跳转到指定页面

功能开启后，在设置弹窗中填写跳转的链接（链接需为包含http://或http://前缀的地址），设置完成后当答题者提交问卷后浏览器将跳转到您设置的链接上。

![](../../.gitbook/assets/image%20%28333%29.png)

![&#x8BBE;&#x7F6E;&#x8DF3;&#x8F6C;&#x5730;&#x5740;](../../.gitbook/assets/image%20%28392%29.png)

## 登录态回调接口

提供登录态回调的功能，开发者可自行配置回调地址和密钥，问卷系统将登录态等参数回调给开发者，开发者获取参数后可用于奖励发放。

![](../../.gitbook/assets/image%20%28448%29.png)

![&#x914D;&#x7F6E;&#x767B;&#x5F55;&#x6001;&#x56DE;&#x8C03;](../../.gitbook/assets/image%20%28339%29.png)



{% hint style="info" %}
### 回调url示例

开发者回调接口url?sid=5da414769e8aa80019305e32×tamp=1573556685&uid=test\_user&user\_type=third\_party&uid\_source=qq&info=afdadsfasdfasdf&callback\_params=callbackparams&sign=38408d6222e1a4c6fa598e4820443ca8
{% endhint %}

[点击了解详细API文档](../../api-wen-dang/deng-lu-tai-hui-tiao-jie-kou.md)。

## API调用

系统提供开放接口用以查询指定问卷的答卷信息、答题统计数据、题型统计等，开启功能后系统将自动生成密钥（密钥支持自定义修改），凭密钥调用接口查询问卷信息；关闭后不可调用查询。

![](../../.gitbook/assets/image%20%28252%29.png)

![](../../.gitbook/assets/image%20%284%29.png)

[点击了解详细API文档。](../../api-wen-dang/kai-fang-jie-kou.md)

## 提交问卷后发奖

支持AMS礼包发奖功能；对于未对接AMS发奖功能的游戏，开启此功能时，用户提交问卷后，问卷系统可自动触发奖励发放。

{% hint style="info" %}
1. 仅支持已对接邮件发奖功能的游戏使用
2. 问卷务必开启[MSDK登录验证](da-ti-xian-zhi-she-zhi.md#msdk-deng-lu-yan-zheng)/[参数传递（严格校验模式）](chuan-can-tiao-zhuan-hui-tiao.md#can-shu-chuan-di-jie-kou-yan-ge-xiao-yan-mo-shi)/[参数传递（不校验模式）](chuan-can-tiao-zhuan-hui-tiao.md#can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)以上任一功能
3. 对每个答题者仅发奖一次；已成功发奖的答题者再次回答问卷后不可二次触发发奖
{% endhint %}

### 【STEP 1】AMS礼包单配置

请在AMS接口平台—礼包仓库\(mrms\)，即道具仓库中配置AMS礼包单，以获取AMS礼包单号、礼包组编号。

{% hint style="danger" %}
注：使用渠道务必配置为 **MUR问卷发奖应用 \[IEG-AMS-11836\]**
{% endhint %}

### 【STEP 2】发奖配置

在需要发奖的问卷中开启“提交问卷后发奖”功能，并配置AMS礼包单号、礼包组编号、业务缩写、AMS环境参数

![&#x914D;&#x7F6E;&#x53D1;&#x5956;&#x53C2;&#x6570;](../../.gitbook/assets/image%20%28564%29.png)

### 【STEP 3】传递发奖参数

问卷务必开启MSDK登录验证/参数传递（严格校验模式）/参数传递（不校验模式）以上任一功能，游戏客户端把以下4个发奖参数用拼接的方式注入问卷链接，用以发奖，参数说明如下：

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x53C2;&#x6570;&#x540D;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p>sPlatId</p>
      </td>
      <td style="text-align:left">&#x5E73;&#x53F0;&#x7C7B;&#x578B;&#xFF0C;&#x5982;IOS:0&#x3001;&#x5B89;&#x5353;:1</td>
    </tr>
    <tr>
      <td style="text-align:left">sArea</td>
      <td style="text-align:left">&#x5BF9;&#x5E94;&#x5230;&#x6E20;&#x9053;&#xFF0C;&#x5982;&#x624B;Q&#x3001;&#x5FAE;&#x4FE1;&#xFF0C;&#x8BF7;&#x4F20;&#x5BF9;&#x5E94;&#x7684;&#x6570;&#x5B57;</td>
    </tr>
    <tr>
      <td style="text-align:left">sPartition</td>
      <td style="text-align:left">&#x624B;&#x673A;&#x7AEF;&#x4F7F;&#x7528;&#xFF0C;&#x5C0F;&#x533A;</td>
    </tr>
    <tr>
      <td style="text-align:left">sRoleId</td>
      <td style="text-align:left">&#x89D2;&#x8272;ID&#xFF0C;&#x53D1;&#x8D27;&#x5230;&#x6E38;&#x620F;&#x5185;&#x65F6;&#x63D0;&#x4F9B;</td>
    </tr>
  </tbody>
</table>

#### 问卷链接注入发奖参数示例

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x60C5;&#x51B5;</th>
      <th style="text-align:left">&#x6CE8;&#x5165;&#x8BF4;&#x660E;</th>
      <th style="text-align:left">&#x793A;&#x4F8B;&#x94FE;&#x63A5;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x539F;&#x59CB;&#x95EE;&#x5377;&#x94FE;&#x63A5;</td>
      <td style="text-align:left">--</td>
      <td style="text-align:left">https://in.survey.imur.tencent.com/?sid=5e8d767b76051f46707cf692&amp;lang=zh-CHS&amp;ADTAG=sid.5e8d767b76051f46707cf692</td>
    </tr>
    <tr>
      <td style="text-align:left">MSDK&#x767B;&#x5F55;&#x9A8C;&#x8BC1;</td>
      <td style="text-align:left">
        <p>4&#x4E2A;&#x53D1;&#x5956;&#x53C2;&#x6570;</p>
        <p>&#x76F4;&#x63A5;&#x62FC;&#x63A5;&#x5728;</p>
        <p>&#x95EE;&#x5377;&#x94FE;&#x63A5;&#x540E;</p>
      </td>
      <td style="text-align:left">https://in.survey.imur.tencent.com/?sid=5e8d767b76051f46707cf692&amp;lang=zh-CHS&amp;ADTAG=sid.5e8d767b76051f46707cf692<b>&amp;sPlatId={sPlatId}&amp;sArea={sArea}&amp;sPartition={sPartition}&amp;sRoleId={sRoleId}</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x53C2;&#x6570;&#x4F20;&#x9012;&#x63A5;&#x53E3;&#xFF08;&#x4E0D;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>4&#x4E2A;&#x53D1;&#x5956;&#x53C2;&#x6570;</p>
        <p>&#x76F4;&#x63A5;&#x62FC;&#x63A5;&#x5728;</p>
        <p>&#x95EE;&#x5377;&#x94FE;&#x63A5;&#x540E;</p>
        </td>
        <td style="text-align:left">https://in.survey.imur.tencent.com/?sid=5e8d767b76051f46707cf692&amp;lang=zh-CHS&amp;ADTAG=sid.5e8d767b76051f46707cf692&amp;openid={&#x7B54;&#x9898;&#x8005;openid}<b>&amp;sPlatId={sPlatId}&amp;sArea={sArea}&amp;sPartition={sPartition}&amp;sRoleId={sRoleId}</b>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x53C2;&#x6570;&#x4F20;&#x9012;&#x63A5;&#x53E3;&#xFF08;&#x4E25;&#x683C;&#x6821;&#x9A8C;&#x6A21;&#x5F0F;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>4&#x4E2A;&#x53D1;&#x5956;&#x53C2;&#x6570;</p>
        <p>&#x62FC;&#x63A5;&#x5728;redirect&#x6240;&#x8D4B;&#x503C;&#x7684;&#x94FE;&#x63A5;&#x540E;&#x518D;&#x5BF9;redirect&#x7684;&#x503C;encode</p>
        </td>
        <td style="text-align:left">
          <p>https:// inapi.survey.imur.tencent.com/autologin?sid</p>
          <p>=5e8d767b76051f46707cf692&amp;uid=user_id&amp;timestamp=1573455797</p>
          <p>&amp;source=dwk&amp;info=extra_info&amp;redirect=https%3A%2F%2F</p>
          <p>in.survey.imur.tencent.com%2F%3Fsid%3D5e8d767b76051f46707cf692</p>
          <p>%26lang%3Dzh-CHS%26ADTAG%3Dsid.5e8d767b76051f46707cf692</p>
          <p><b>%26sPlatId%3D{sPlatId}%26sArea%3D{sArea}%26sPartition</b>
          </p>
          <p><b>%3D{sPartition}%26sRoleId%3D{sRoleId}</b>
          </p>
          <p>&amp;sign=2ac5ab8ce6a9b306e07dc2664fe7d175</p>
        </td>
    </tr>
  </tbody>
</table>

### 【STEP 4】完成

在游戏中投放问卷，答题者提交问卷后，问卷系统会自动触发调用AMS礼包单发奖。

