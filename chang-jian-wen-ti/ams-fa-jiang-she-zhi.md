# 答题自动发奖

## 问卷可以实现用户填完问卷后发奖的功能吗？

系统支持AMS礼包发奖，可通过问卷设置—提交问卷后发奖功能实现；对于已对接AMS邮件发货功能的游戏，开启此功能时，用户提交问卷后，问卷系统可自动触发奖励发放。

![提交问卷后发奖](<../.gitbook/assets/image (566).png>)

{% hint style="info" %}
1. 仅支持已对接**邮件发货**功能的游戏使用
2. 问卷务必开启[MSDK登录验证](../cao-zuo-zhi-yin/wen-juan-she-zhi/da-ti-xian-zhi-she-zhi/#msdk-deng-lu-yan-zheng)/[参数传递（严格校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao.md#can-shu-chuan-di-jie-kou-yan-ge-xiao-yan-mo-shi)/[参数传递（不校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao.md#can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)以上任一功能
3. 对每个答题者仅发奖一次；已成功发奖的答题者再次回答问卷后不可二次触发发奖
{% endhint %}

### 【STEP 1】AMS礼包单配置

请在AMS接口平台—礼包仓库(mrms)，即道具仓库中配置AMS礼包单，以获取AMS礼包单号、礼包组编号。

{% hint style="danger" %}
注：使用渠道务必配置为 **MUR问卷发奖应用 \[IEG-AMS-11836]**
{% endhint %}

### 【STEP 2】发奖配置

在需要发奖的问卷中开启“提交问卷后发奖”功能，并配置AMS礼包单号、礼包组编号、业务缩写、AMS环境参数

![配置发奖参数](<../.gitbook/assets/image (565).png>)

### 【STEP 3】传递发奖参数

问卷务必开启MSDK登录验证/参数传递（严格校验模式）/参数传递（不校验模式）以上任一功能，游戏客户端把以下4个发奖参数用拼接的方式注入问卷链接，用以发奖，参数说明如下：

| 参数名                   | 说明                   |
| --------------------- | -------------------- |
| <p></p><p>sPlatId</p> | 平台类型，如IOS:0、安卓:1     |
| sArea                 | 对应到渠道，如手Q、微信，请传对应的数字 |
| sPartition            | 手机端使用，小区             |
| sRoleId               |  角色ID，发货到游戏内时提供      |

#### 问卷链接注入发奖参数示例

| 情况             | 注入说明                                                     | 示例链接                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| -------------- | -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 原始问卷链接         | --                                                       | https://in.survey.imur.tencent.com/?sid=5e8d767b76051f46707cf692                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| MSDK登录验证       | <p>4个发奖参数</p><p>直接拼接在</p><p>问卷链接后</p>                    | https://in.survey.imur.tencent.com/?sid=5e8d767b76051f46707cf692**\&sPlatId={sPlatId}\&sArea={sArea}\&sPartition={sPartition}\&sRoleId={sRoleId}**                                                                                                                                                                                                                                                                                                                                                                                             |
| 参数传递接口（不校验模式）  | <p>4个发奖参数</p><p>直接拼接在</p><p>问卷链接后</p>                    | https://in.survey.imur.tencent.com/?sid=5e8d767b76051f46707cf692\&openid={答题者openid}**\&sPlatId={sPlatId}\&sArea={sArea}\&sPartition={sPartition}\&sRoleId={sRoleId}**                                                                                                                                                                                                                                                                                                                                                                         |
| 参数传递接口（严格校验模式） | <p>4个发奖参数</p><p>拼接在redirect所赋值的链接后再对redirect的值encode</p> | <p>https:// inapi.survey.imur.tencent.com/autologin?sid</p><p>=5e8d767b76051f46707cf692&#x26;uid=user_id&#x26;timestamp=1573455797</p><p>&#x26;source=dwk&#x26;info=extra_info&#x26;redirect=https%3A%2F%2F</p><p>in.survey.imur.tencent.com%2F%3Fsid%3D5e8d767b76051f46707cf692</p><p>%26lang%3Dzh-CHS%26ADTAG%3Dsid.5e8d767b76051f46707cf692</p><p><strong>%26sPlatId%3D{sPlatId}%26sArea%3D{sArea}%26sPartition</strong></p><p><strong>%3D{sPartition}%26sRoleId%3D{sRoleId}</strong></p><p>&#x26;sign=2ac5ab8ce6a9b306e07dc2664fe7d175</p> |

### 【STEP 4】接口申请

由问卷触发ams发奖需提前申请游戏内抽奖接口，请企业微信联系：IMUR问卷系统助手

### 【STEP 5】完成

在游戏中投放问卷，答题者提交问卷后，问卷系统会自动触发调用AMS礼包单发奖（奖品名称显示为step1中所配置的礼包组名称）。

![游戏内填答后发奖成功提示](<../.gitbook/assets/image (563).png>)

## 在问卷设置中配置了AMS礼包单，为什么提交问卷后还是领不到奖励？

请确保满足以下条件，才能成功发奖：

1. 已开启[MSDK登录验证](../cao-zuo-zhi-yin/wen-juan-she-zhi/da-ti-xian-zhi-she-zhi/#msdk-deng-lu-yan-zheng)/[参数传递（严格校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao.md#can-shu-chuan-di-jie-kou-yan-ge-xiao-yan-mo-shi)/[参数传递（不校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao.md#can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)以上任一功能
2. 传递的玩家openid正确（参数传递的openid请赋值为玩家的游戏openid，如：oprwpv50pyA2Ts4C14P3NvqSN1q5，非纯数字的gopenid，转换接口可参考[https://docs.itop.qq.com/v5/zh-CN/Server/openid2uid.html](https://docs.itop.qq.com/v5/zh-CN/Server/openid2uid.html)）
3. 传递的发奖参数sPlatId、sArea、sPartition、sRoleId正确
4. 游戏内的邮件发奖功能可用
5. 该答题者是首次在该问卷中领取奖励
