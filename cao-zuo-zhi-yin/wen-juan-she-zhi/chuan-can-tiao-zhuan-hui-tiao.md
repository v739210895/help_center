# API\(跳转/回调/发奖）

问卷系统支持内嵌投放及答题后跳转、参数回调等功能，用户可根据实际需要按以下各项设置。

![API&#x914D;&#x7F6E;](../../.gitbook/assets/image%20%28672%29.png)

## 提交问卷跳转到指定页面

功能开启后，在设置弹窗中填写跳转的链接（链接需为包含http://或http://前缀的地址），设置完成后当答题者提交问卷后浏览器将跳转到您设置的链接上。

![&#x529F;&#x80FD;&#x6D41;&#x7A0B;](../../.gitbook/assets/image%20%28333%29.png)

![&#x8BBE;&#x7F6E;&#x8DF3;&#x8F6C;&#x5730;&#x5740;](../../.gitbook/assets/image%20%28658%29.png)

## 登录态回调接口

提供登录态回调的功能，开发者可自行配置回调地址和密钥，问卷系统将登录态等参数回调给开发者，开发者获取参数后可用于奖励发放。

![&#x64CD;&#x4F5C;&#x6D41;&#x7A0B;](../../.gitbook/assets/image%20%28448%29.png)

![&#x914D;&#x7F6E;&#x767B;&#x5F55;&#x6001;&#x56DE;&#x8C03;](../../.gitbook/assets/image%20%28653%29.png)

### 同一问卷支持设置多个回调地址

投放时**客户端**在问卷链接中注入callback参数，用以区分该次提交后回调到哪个回调地址中。最多可配置10个回调地址，具体回调到哪个实际由客户端指定。

**注：**每次提交问卷仅能回调到一个地址中，若问卷链接未注入callback参数，默认回调到地址1。

{% hint style="info" %}
如投放链接中注入callback的值为2，则提交后系统自动把登录态信息回调到回调地址2中

https://in.weisurvey.com/?sid=5f87b81376051f331039dfe5&openid={openid}**&callback=2**
{% endhint %}

![&#x591A;&#x4E2A;&#x56DE;&#x8C03;&#x5730;&#x5740;&#x914D;&#x7F6E;&#x793A;&#x4F8B;](../../.gitbook/assets/image%20%28654%29.png)

### 回调示例

开发者回调接口url?sid=5da414769e8aa80019305e32&timestamp=1573556685&uid=test\_user&user\_type=third\_party&uid\_source=qq&info=afdadsfasdfasdf&callback\_params=callbackparams&sign=38408d6222e1a4c6fa598e4820443ca8

[点击了解详细API文档](../../api-wen-dang/deng-lu-tai-hui-tiao-jie-kou.md)。

## API调用

系统提供开放接口用以查询指定问卷的答卷信息、答题统计数据、题型统计等，开启功能后系统将自动生成密钥（密钥支持自定义修改），凭密钥调用接口查询问卷信息；关闭后不可调用查询。

![](../../.gitbook/assets/image%20%28252%29.png)

![](../../.gitbook/assets/image%20%284%29.png)

[点击了解详细API文档。](../../api-wen-dang/kai-fang-jie-kou/)

## 提交问卷后发奖

支持AMS礼包发奖功能；对于未对接AMS发奖功能的游戏，开启此功能时，用户提交问卷后，问卷系统可自动触发奖励发放。

{% hint style="info" %}
1. 仅支持已对接**邮件发货**功能的游戏使用
2. 问卷务必开启[MSDK登录验证](da-ti-xian-zhi-she-zhi/#msdk-deng-lu-yan-zheng)/[参数传递（严格校验模式）](chuan-can-tiao-zhuan-hui-tiao.md#can-shu-chuan-di-jie-kou-yan-ge-xiao-yan-mo-shi)/[参数传递（不校验模式）](chuan-can-tiao-zhuan-hui-tiao.md#can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)以上任一功能
3. 对每个答题者仅发奖一次；已成功发奖的答题者再次回答问卷后不可二次触发发奖
{% endhint %}

### 【STEP 1】AMS礼包单配置

请在AMS接口平台—礼包仓库\(mrms\)，即道具仓库中配置AMS礼包单，以获取AMS礼包单号、礼包组编号。

{% hint style="danger" %}
注：使用渠道务必配置为 **MUR问卷发奖应用 \[IEG-AMS-11836\]**
{% endhint %}

### 【STEP 2】发奖配置

在需要发奖的问卷中开启“提交问卷后发奖”功能，并配置AMS礼包单号、礼包组编号、业务缩写、AMS环境参数

![&#x914D;&#x7F6E;&#x53D1;&#x5956;&#x53C2;&#x6570;](../../.gitbook/assets/image%20%28565%29.png)

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

### 【STEP 4】接口申请

由问卷触发ams发奖需提前申请游戏内抽奖接口，请企业微信联系：IMUR问卷系统助手

### 【STEP 5】完成

在游戏中投放问卷，答题者提交问卷后，问卷系统会自动触发调用AMS礼包单发奖（奖品名称显示为step1中所配置的礼包组名称）。

![&#x6E38;&#x620F;&#x5185;&#x586B;&#x7B54;&#x540E;&#x53D1;&#x5956;&#x6210;&#x529F;&#x63D0;&#x793A;](../../.gitbook/assets/image%20%28563%29.png)

