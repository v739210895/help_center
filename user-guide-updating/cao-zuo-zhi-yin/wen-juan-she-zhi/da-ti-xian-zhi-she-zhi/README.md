# Survey Response Limit Settings

<figure><img src="../../../../.gitbook/assets/image (1003).png" alt=""><figcaption></figcaption></figure>

## Each user ID can only answer once

This feature requires verification via WeChat, QQ login, or MSDK login. Once enabled, it will check whether the user has already completed the survey based on their user ID. If they have already completed it, the survey cannot be opened. The message for attempting to retake the survey will be displayed in the language set for the survey.

![Duplicate survey response warning](<../../../../.gitbook/assets/image (48).png>)

### Each IP can only answer once

{% hint style="danger" %}
This feature is not yet available
{% endhint %}

Once the feature is enabled, the survey will verify the user’s IP when opened. If the user has already answered the survey, they will be prohibited from responding a second time.

### Each browser can only answer once.

After the feature is enabled, it will determine whether the user has already completed the survey based on the user's current browser identifier. If the user has completed the survey, they will be prohibited from opening the survey.

{% hint style="info" %}
If the user clears the browser cache, they can answer the survey again.
{% endhint %}

## Whitelist survey restriction

After the feature is enabled, the system will first check if the current respondent is a whitelist user when opening the survey. Only whitelist users can access the survey.

![Whitelist Authentication](<../../../../.gitbook/assets/image (372).png>)

{% hint style="info" %}
The whitelist file size limit is 10MB; there is no limit on the number of whitelist users. You can refer to:

【openid】 (22 characters): Can upload approximately 300,000

\[QQ number] (9 digits): Can upload approximately 750,000

\[Phone Number] (11 digits): can upload approximately 600,000
{% endhint %}

### Whitelist File Rules Description

QQ number/Phone number

Directly write the QQ number/phone number of the whitelist user, one number per line.

#### openid

Directly write the openid of whitelisted users, one number per line, and use it with any of the following login functions.

| Login verification method             | Explanation of openid value                                                                                                                                                                                                                                                                                                             | Example Value                                                                                 |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| WeChat, QQ login verification         | The openid (non-game openid) that users obtain after logging into the survey through WeChat/QQ,Please refer to the method for converting QQ number to openid.[QQ号转openid](https://imur.gitbook.io/help_center/chang-jian-wen-ti/uidopenid-zhuan-huan-qq-hao#fu-lu-openid-shi-shen-me-ying-yong-nei-yong-hu-shen-fen-de-wei-yi-biao-shi) | <p>【QQ】78F2938728791F866806043CEFF5222D</p><p>【WeChat】</p><p>oY2--whSvI7JPzmQWcRg7o60TpdQ</p> |
| MSDKv3                                | Players openid in the game                                                                                                                                                                                                                                                                                                              | 56C589029A4C0BD2282D5CD2DD5725F2                                                              |
| MSDKv5                                | Players openid in the game                                                                                                                                                                                                                                                                                                              | 13293484783071200846                                                                          |
| Parameter Passing (Strict Validation) | The uid value when passing parameters (customized by the game), for details please refer to[参数传递接口（严格校验模式）](../../../../api-wen-dang/fei-msdk-deng-lu-tai-chuan-di-jie-kou.md)                                                                                                                                                          | 30291658356950347                                                                             |
| Parameter Passing (No Validation)     | The openid value when passing parameters (customized by the game), for more details please refer to[参数传递接口（不校验模式）](../../../../api-wen-dang/can-shu-chuan-di-jie-kou-bu-xiao-yan-mo-shi.md)                                                                                                                                             | 30291658356950347                                                                             |

