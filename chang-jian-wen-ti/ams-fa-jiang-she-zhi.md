# 答题自动发奖

## 问卷可以实现用户填完问卷后发奖的功能吗？

系统支持AMS礼包发奖，可通过问卷设置—提交问卷后发奖功能实现；对于已对接AMS邮件发货功能的游戏，开启此功能时，用户提交问卷后，问卷系统可自动触发奖励发放。

![提交问卷后发奖](<../.gitbook/assets/image (483).png>)

<img src="../.gitbook/assets/image (2).png" alt="发奖成功效果" data-size="original">



## 配置步骤

请点击查看：[提交问卷后发奖](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao/#ti-jiao-wen-juan-hou-fa-jiang)



## 特殊说明

{% hint style="info" %}
1. 仅支持已对接**邮件发货**功能的游戏（国内版）使用
2. 问卷务必开启[MSDK登录验证](../cao-zuo-zhi-yin/wen-juan-she-zhi/da-ti-xian-zhi-she-zhi/#msdk-deng-lu-yan-zheng)/[参数传递（严格校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao/#can-shu-chuan-di-jie-kou-yan-ge-xiao-yan-mo-shi)/[参数传递（不校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao/#can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)以上任一功能
3. 对每个答题者仅发奖一次；已成功发奖的答题者再次回答问卷后不可二次触发发奖
{% endhint %}



## 在问卷设置中配置了AMS礼包单，为什么提交问卷后还是领不到奖励？

请确保满足以下条件，才能成功发奖：

1. 已开启[MSDK登录验证](../cao-zuo-zhi-yin/wen-juan-she-zhi/da-ti-xian-zhi-she-zhi/#msdk-deng-lu-yan-zheng)/[参数传递（严格校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao/#can-shu-chuan-di-jie-kou-yan-ge-xiao-yan-mo-shi)/[参数传递（不校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao/#can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)以上任一功能
2. 传递的玩家openid正确（参数传递的openid请赋值为玩家的游戏openid，如：oprwpv50pyA2Ts4C14P3NvqSN1q5，非纯数字的gopenid，转换接口可参考[https://docs.itop.qq.com/v5/zh-CN/Server/openid2uid.html](https://docs.itop.qq.com/v5/zh-CN/Server/openid2uid.html)）
3. 传递的发奖参数sPlatId、sArea、sPartition、sRoleId正确
4. 游戏内的邮件发奖功能可用
5. 该答题者是首次在该问卷中领取奖励
