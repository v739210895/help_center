---
hidden: true
---

# API Documentation

系统为游戏提供多种内嵌功能，可用于采集玩家openid、答题后实时通知游戏、奖励发放等。

自助接入请先填写《内嵌联调信息登记及方案建议》[https://in.weisurvey.com/v2/?sid=5f589c6e76051fa2a616a549](https://in.weisurvey.com/v2/?sid=5f589c6e76051fa2a616a549)，根据卷末推荐方案自助接入；接入过程中如有疑问请咨询：IMUR问卷系统助手。

{% hint style="info" %}
流程实现及实例介绍可参考[https://docs.qq.com/slide/DSlR6WExqemZub092](https://docs.qq.com/slide/DSlR6WExqemZub092)
{% endhint %}

![实例流程介绍](<../../.gitbook/assets/image (134).png>)

## 【附】API文档目录

| 场景                                                         | 使用接口                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 采集内嵌投放的用户openid                                            | <p><a href="../../api-wen-dang/msdkv3-deng-lu-tai-cai-ji.md">MSDK v3登录态采集</a><br><a href="../../api-wen-dang/msdkv5-deng-lu-tai-cai-ji.md">MSDK v5登录态采集</a><br><a href="../../api-wen-dang/intl-deng-lu-tai-cai-ji.md">INTL登录态采集</a><br><a href="../../api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou.md">参数传递接口（严格校验模式）</a><br><a href="../../api-wen-dang/can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi.md">参数传递接口（不校验模式）</a></p> |
| <p>开发者后端回调完成答题用户openid，透传参数等，</p><p>用于发奖、隐藏APP内问卷按钮等场景</p> | [登录态回调接口](../../api-wen-dang/deng-lu-tai-hui-tiao-jie-kou.md)                                                                                                                                                                                                                                                                                                                                                                         |
| 用户提交问卷后，由问卷系统触发ams礼包发放                                     | [AMS发奖](../../api-wen-dang/idip-fa-jiang.md)                                                                                                                                                                                                                                                                                                                                                                                          |
| 开发者获取问卷题目内容和统计结果等                                          | [开放接口](../../api-wen-dang/kai-fang-jie-kou/)                                                                                                                                                                                                                                                                                                                                                                                          |

