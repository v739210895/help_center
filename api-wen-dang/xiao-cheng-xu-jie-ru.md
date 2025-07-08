# 小程序接入

打开问卷小程序（使用于小游戏/小程序）

#### 主要流程 <a href="#e4-b8-bb-e8-a6-81-e6-b5-81-e7-a8-8b" id="e4-b8-bb-e8-a6-81-e6-b5-81-e7-a8-8b"></a>

小游戏 -> 打开问卷小程序 + 传参（问卷ID/用户信息等）-> 小程序加载web-view -> 拼接参数生成url并加载问卷

#### 参考文档 <a href="#e5-8f-82-e8-80-83-e6-96-87-e6-a1-a3" id="e5-8f-82-e8-80-83-e6-96-87-e6-a1-a3"></a>

[小游戏打开小程序](https://developers.weixin.qq.com/minigame/dev/api/navigate/wx.navigateToMiniProgram.html)

小游戏通过调用微信小程序官方提供的API wx.navigateToMiniProgram 打开微信小程序

#### 调用方式 <a href="#e8-b0-83-e7-94-a8-e6-96-b9-e5-bc-8f" id="e8-b0-83-e7-94-a8-e6-96-b9-e5-bc-8f"></a>

```js
wx.navigateToMiniProgram({
  appId: 'wx149846fa7a7da33c',
  path: 'pages/index/index',
  extraData: {
    surveyId: '656556d8426fb8a9f901dc12', // 问卷ID
    urlQuery: 'sPlatId=xx&sArea=xx&sPartition=xx&sRoleId=xx', // url 的 Query参数
    uid: 'xxx', // 用户的唯一标识
  },
  success(res) {
    // 打开成功
  },
  fail() {
    // 打开失败
  }
})
```

[小程序通过半屏打开目标小程序](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.openEmbeddedMiniProgram.html)

小程序通过调用微信小程序官方提供的API wx.openEmbeddedMiniProgram 半屏打开目标小程序

#### 调用方式 <a href="#e8-b0-83-e7-94-a8-e6-96-b9-e5-bc-8f-3" id="e8-b0-83-e7-94-a8-e6-96-b9-e5-bc-8f-3"></a>

```js
wx.openEmbeddedMiniProgram({
  appId: 'wx149846fa7a7da33c',
  path: 'pages/index/index',
  extraData: {
    surveyId: '656556d8426fb8a9f901dc12', // 问卷ID
    urlQuery: 'sPlatId=xx&sArea=xx&sPartition=xx&sRoleId=xx', // url 的 Query参数
    uid: 'xxx', // 用户的唯一标识
	env: 'production', // production生产环境/test测试环境, 默认为production 
  },
  success(res) {
    // 打开成功
  },
  fail() {
    // 打开失败
  }
})
```

extraData 参数说明:

| 参数       | 说明                     | 是否必需 |
| -------- | ---------------------- | ---- |
| surveyId | 问卷ID                   | 是    |
| urlQuery | 打开问卷时候自定义的 Url Query参数 | 否    |
| uid      | 用户的唯一标识，用于问卷非严格模式登录    | 否    |
| env      | 使用环境                   | 否    |

&#x20;

小游戏不支持通过半屏去打开微信小程序 (小游戏官方文档没有可调用的半屏打开API)

#### 小游戏测试案例 <a href="#e5-b0-8f-e6-b8-b8-e6-88-8f-e6-b5-8b-e8-af-95-e6-a1-88-e4-be-8b" id="e5-b0-8f-e6-b8-b8-e6-88-8f-e6-b5-8b-e8-af-95-e6-a1-88-e4-be-8b"></a>

&#x20;

![企业微信截图\_20231221170331.png](https://iwiki.woa.com/tencent/api/attachments/s3/url?attachmentid=16825986)\
![企业微信截图\_20231221170351.png](https://iwiki.woa.com/tencent/api/attachments/s3/url?attachmentid=16825994)

&#x20;

