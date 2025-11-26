# 内嵌问卷SDK-原生接入指南

### 快速上手 <a href="#kuai-su-shang-shou" id="kuai-su-shang-shou"></a>

1. 解压下载的定制发布压缩包
2. 参看接入说明选择需要接入的平台

### 下载最新的SDK

在 Release 中找到最新版本 ，[releases](https://git.woa.com/mur-survey/SurveyPopupView/-/releases)\
下载附件 `imursurvey_popupview_native.zip`

> 默认构建 iOS 未开启 BITCODE，Android 默认剔除 X5\_SDK ，如有问题，请线下联系出包

压缩包目录结构如下

```
Assets
├── Plugins
│   ├── Android
│   │   ├── SurveyPopupView.aar
│   │   └── SurveyPopupView.aar.meta
│   ├── Android.meta
│   ├── iOS
│   │   ├── SurveyPopupView.framework
│   │   └── SurveyPopupView.framework.meta
│   └── iOS.meta
```

### 接入说明 <a href="#jie-ru-shuo-ming" id="jie-ru-shuo-ming"></a>

#### Android项目集成 <a href="#android-xiang-mu-ji-cheng" id="android-xiang-mu-ji-cheng"></a>

1、从解压的文件夹**Assets/Plugins/Android**目录下把**SurveyPopupView.aar**复制到android工程代码根目录下的**app/libs**目录中

<figure><img src="../.gitbook/assets/image (819).png" alt=""><figcaption></figcaption></figure>

2、检查build.gradle文件中的dependencies是否有包加载配置，如没有请添加一下代码：

implementation fileTree(dir: 'libs', include: \['\*.jar','\*.aar'])

<figure><img src="../.gitbook/assets/image (820).png" alt=""><figcaption></figcaption></figure>

3、由于问卷的sdk依赖x5，请检查proguard-rules.pro文件中有添加以下混淆配置：

```
-keep class com.tencent.imur.** { *; }
-keep class com.tencent.smtt.** { *; }
```

<figure><img src="../.gitbook/assets/image (821).png" alt=""><figcaption></figcaption></figure>

#### IOS项目集成 <a href="#ios-xiang-mu-ji-cheng" id="ios-xiang-mu-ji-cheng"></a>

1、打开xcode，从解压的文件夹**Assets/Plugins/IOS**目录下把**SurveyPopupView.framework**拖拽或者File → Add Files to xxx 添加到到ios工程代码根目录下

<figure><img src="../.gitbook/assets/image (822).png" alt=""><figcaption></figcaption></figure>

2、在TARGET的General配置下启用framework的集成：<br>

<figure><img src="../.gitbook/assets/image (823).png" alt=""><figcaption></figcaption></figure>

确保Build Settings下Runpath Search Paths能找到改framework：

<figure><img src="../.gitbook/assets/image (824).png" alt=""><figcaption></figcaption></figure>

3、运行，正常情况下能编译通过。

### Android API <a href="#android-api" id="android-api"></a>

sdk对外的API在com.tencent.imur.survey.IMurSurveyAdapter类中，主要API说明：

**1、打开问卷弹窗**

<pre data-line-numbers><code><strong>import android.app.Activity;
</strong>import com.tencent.imur.survey.IMurSurveyAdapter;

Activity app = this; // 打开弹窗需要的activity
String surveyID = "<a data-footnote-ref href="#user-content-fn-1">6350b6a987ee34f6e6025c02</a>"; // 问卷SID
String urlParams = "<a data-footnote-ref href="#user-content-fn-1">openid=xxx&#x26;info=xxx"</a>; // 登陆态等信息
IMurSurveyAdapter.openSurvey(app, surveyID, urlParams);
</code></pre>

urlParams参数请参考下方【打开问卷弹窗参数】

**2、设置问卷参数**

<pre data-line-numbers><code>import com.tencent.imur.survey.IMurSurveyAdapter;
import org.json.JSONObject;

JSONObject conf = new JSONObject();
conf.put("<a data-footnote-ref href="#user-content-fn-1">mask</a>", true);
String configJson = conf.toString();
IMurSurveyAdapter.setSurveyConfig(configJson);
</code></pre>

surveyConfig参数请参考下【问卷配置参数】

**3、关闭问卷弹窗**

{% code lineNumbers="true" %}
```
import com.tencent.imur.survey.IMurSurveyAdapter;

IMurSurveyAdapter.close();
```
{% endcode %}

一般不需要使用，因为问卷本身的弹窗有关闭功能。

### IOS API <a href="#ios-api" id="ios-api"></a>

导入 SurveyPopupView.framework 之后，通过 \`#import \<SurveyPopupView/SurveyPopupView.h>\` 方式引入头文件，SurveyPopupView 会暴露 3 个主要的静态方法。

**1、打开问卷弹窗**

{% code lineNumbers="true" %}
```
#import <SurveyPopupView/SurveyPopupView.h>

[SurveyPopupView openSurvey:@"6486e8655e4f942e4507f9e3" params:@"openid=xxx&info=xxx"];
```
{% endcode %}

params参数请参考下方【打开问卷弹窗参数】

**2、设置问卷参数**

{% code lineNumbers="true" %}
```
#import <SurveyPopupView/SurveyPopupView.h>

NSMutableDictionary *dict = [NSMutableDictionary dictionary];
dict[@"surveyEnv"] = @"oversea";

// 将 NSMutableDictionary 转换成 JSON 数据
NSError *error = nil;
NSData *jsonData = [NSJSONSerialization dataWithJSONObject:dict
                                                   options:0 // 没有特殊的格式化选项
                                                     error:&error];
if (!jsonData) {
    NSLog(@"JSON 序列化错误: %@", error);
} else {
    // 将 JSON 数据转换成 NSString
    NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];
    [SurveyPopupView setSurveyConfig:jsonString];
}
```
{% endcode %}

setSurveyConfig 参数请参考下【问卷配置参数】

**3、关闭问卷弹窗**

```
#import <SurveyPopupView/SurveyPopupView.h>

[SurveyPopupView close];
```

一般不需要使用，因为问卷本身的弹窗有关闭功能。

#### 打开问卷弹窗参数 <a href="#da-kai-wen-juan-tan-chuang-can-shu" id="da-kai-wen-juan-tan-chuang-can-shu"></a>

<table data-header-hidden><thead><tr><th width="128"></th><th width="163"></th><th width="194"></th><th></th></tr></thead><tbody><tr><td>参数</td><td>说明</td><td>格式</td><td>示例</td></tr><tr><td>surveyId</td><td>问卷sid</td><td>问卷投放链接中的sid参数的值</td><td>6350b6a987ee34f6e6025c02</td></tr><tr><td>urlparams</td><td>url query (非必填)</td><td>参数名1=参数值 &#x26; 参数2=参数值 &#x26; …</td><td>openid=xxx&#x26;info=xxx</td></tr></tbody></table>

&#x20;

开发者通过urlparams，实现登录态传递和其他参数传递，部分参数可存储到问卷系统中，部分参数仅做回调透传。

| 参数               | 说明                                               | **数据使用方式**    |
| ---------------- | ------------------------------------------------ | ------------- |
| openid （登录验证时必填） | 登录用户的唯一id                                        | 存储到问卷中，用户ID   |
| channel          | 用户自定义渠道，例如wx/qq等，记录到答题数据中                        | 存储到问卷中，用户ID渠道 |
| info             | 额外的登录用户信息，可自定义。info值会记录到答题数据中的“自定义内容”字段。         | 存储到问卷中，自定义内容列 |
| source           | 用户自定义渠道标识，例如wx/qq等（仅在回调参数中返回，如需记录到答案，请使用channel） | 回调使用，不存储      |
| callback\_params | 开发者自定义回调参数，业务需要额外的参数则可以使用                        | 回调使用，不存储      |

&#x20;

#### 问卷配置参数 <a href="#wen-juan-pei-zhi-can-shu" id="wen-juan-pei-zhi-can-shu"></a>

配置详细列表:

| 参数                | 说明                    | 默认值        |                                                                                                              |
| ----------------- | --------------------- | ---------- | ------------------------------------------------------------------------------------------------------------ |
| primaryColor      | 主题色，最后两个字符表示 alpha 通道 | #18C68AFF  | <p><img src="https://iwiki.woa.com/tencent/api/attachments/s3/url?attachmentid=18794503" alt=""></p><p> </p> |
| bgColor           | 背景色，最后两个字符表示 alpha 通道 | #FFFFFFFF  |                                                                                                              |
| loadingColor      | loading指示条的颜色         | #FFFFFFFF  |                                                                                                              |
| defaultTitle      | sdk标题                 | MUR Survey | <p><img src="https://iwiki.woa.com/tencent/api/attachments/s3/url?attachmentid=18794498" alt=""></p><p> </p> |
| loadingFailedText | 加载失败的文案               | 问卷内容加载失败   | <p><img src="https://iwiki.woa.com/tencent/api/attachments/s3/url?attachmentid=18794499" alt=""></p><p> </p> |
| closeText         | 关闭按钮文案                | 关闭         | <p><img src="https://iwiki.woa.com/tencent/api/attachments/s3/url?attachmentid=18794506" alt=""></p><p> </p> |
| loadingText       | 加载中的文案                | 内容加载中...   | <p><img src="https://iwiki.woa.com/tencent/api/attachments/s3/url?attachmentid=18794509" alt=""></p><p> </p> |
| popupHeightRatio  | 弹窗高度相对于屏幕的高度占比        | 0.85       |                                                                                                              |
| mask              | 是否显示遮罩                | false      |                                                                                                              |

&#x20;

&#x20;

[^1]: 
