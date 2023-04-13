# 在问卷设置中配置了AMS礼包单，为什么提交问卷后还是领不到奖励？

请确保满足以下条件，才能成功发奖：

1. 已开启[MSDK登录验证](../cao-zuo-zhi-yin/wen-juan-she-zhi/da-ti-xian-zhi-she-zhi/#msdk-deng-lu-yan-zheng)/[参数传递（严格校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao/#can-shu-chuan-di-jie-kou-yan-ge-xiao-yan-mo-shi)/[参数传递（不校验模式）](../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao/#can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi)以上任一功能
2. 传递的玩家openid正确（参数传递的openid请赋值为玩家的游戏openid，如：oprwpv50pyA2Ts4C14P3NvqSN1q5，非纯数字的gopenid，转换接口可参考[https://docs.itop.qq.com/v5/zh-CN/Server/openid2uid.html](https://docs.itop.qq.com/v5/zh-CN/Server/openid2uid.html)）
3. 传递的发奖参数sPlatId、sArea、sPartition、sRoleId正确
4. 游戏内的邮件发奖功能可用
5. 该答题者是首次在该问卷中领取奖励
