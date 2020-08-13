# 答题自动发奖

## 问卷可以实现用户填完问卷后发奖的功能吗？

系统支持AMS礼包发奖，可通过问卷设置—提交问卷后发奖功能实现；对于未对接AMS发奖功能的游戏，开启此功能时，用户提交问卷后，问卷系统可自动触发奖励发放。

![&#x63D0;&#x4EA4;&#x95EE;&#x5377;&#x540E;&#x53D1;&#x5956;](../.gitbook/assets/image%20%28566%29.png)

{% hint style="info" %}
1. 仅支持已对接邮件发奖功能的游戏使用
2. 问卷务必开启[MSDK登录验证](../cao-zuo-zhi-yin/wen-juan-she-zhi/da-ti-xian-zhi-she-zhi.md#msdk-deng-lu-yan-zheng)/[参数传递（严格校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao.md#can-shu-chuan-di-jie-kou-yan-ge-xiao-yan-mo-shi)/[参数传递（不校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao.md#can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)以上任一功能
3. 对每个答题者仅发奖一次；已成功发奖的答题者再次回答问卷后不可二次触发发奖
{% endhint %}

### 【STEP 1】AMS礼包单配置

请在AMS接口平台—礼包仓库\(mrms\)，即道具仓库中配置AMS礼包单，以获取AMS礼包单号、礼包组编号。

{% hint style="danger" %}
注：使用渠道务必配置为 **MUR问卷发奖应用 \[IEG-AMS-11836\]**
{% endhint %}

### 【STEP 2】发奖配置

在需要发奖的问卷中开启“提交问卷后发奖”功能，并配置AMS礼包单号、礼包组编号、业务缩写、AMS环境参数

![&#x914D;&#x7F6E;&#x53D1;&#x5956;&#x53C2;&#x6570;](../.gitbook/assets/image%20%28565%29.png)

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

在游戏中投放问卷，答题者提交问卷后，问卷系统会自动触发调用AMS礼包单发奖（奖品名称显示为step1中所配置的礼包组名称）。

![&#x6E38;&#x620F;&#x5185;&#x586B;&#x7B54;&#x540E;&#x53D1;&#x5956;&#x6210;&#x529F;&#x63D0;&#x793A;](../.gitbook/assets/image%20%28563%29.png)

## 在问卷设置中配置了AMS礼包单，为什么提交问卷后还是领不到奖励？

请确保满足以下条件，才能成功发奖：

1. 已开启[MSDK登录验证](../cao-zuo-zhi-yin/wen-juan-she-zhi/da-ti-xian-zhi-she-zhi.md#msdk-deng-lu-yan-zheng)/[参数传递（严格校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao.md#can-shu-chuan-di-jie-kou-yan-ge-xiao-yan-mo-shi)/[参数传递（不校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao.md#can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)以上任一功能
2. 传递的玩家openid正确（参数传递的openid请赋值为玩家的游戏openid，如：oprwpv50pyA2Ts4C14P3NvqSN1q5，非纯数字的gopenid，转换接口可参考[https://docs.itop.qq.com/v5/zh-CN/Server/openid2uid.html](https://docs.itop.qq.com/v5/zh-CN/Server/openid2uid.html)）
3. 传递的发奖参数sPlatId、sArea、sPartition、sRoleId正确
4. 游戏内的邮件发奖功能可用
5. 该答题者是首次在该问卷中领取奖励

