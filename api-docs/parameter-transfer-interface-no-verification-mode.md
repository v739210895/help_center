# Parameter Transfer Interface (Non-Verification Mode)

### Interface Description

#### Interface definition <a href="#jie-kou-ding-yi" id="jie-kou-ding-yi"></a>

The **parameter transfer interface (non-verification mode)** interface is used to &#x20;

(1) third-party developers have their own login status (such as facebook id, Game user id, etc.), but they want to send the login status to the questionnaire system;

(2) Non-standard access to MSDK, result in the failure in collecting the openid with MSDK-V3 or MSDK-V5 .

#### &#x20;<a href="#jie-kou-shuo-ming-1" id="jie-kou-shuo-ming-1"></a>

#### Interface Description <a href="#jie-kou-shuo-ming-1" id="jie-kou-shuo-ming-1"></a>

The developer dynamically splices the specified parameters into the questionnaire link, realizes the login state transfer and other parameter transfer, and stores them in the questionnaire system. The parameters include openid (required), source (optional), info (optional), respectively Stored in the uid, uidSource, and info columns in the exported data.

| Parameter | Required | Description                                              |
| --------- | -------- | -------------------------------------------------------- |
| openid    | Yes      | The unique ID of the logged-in user                      |
| source    | no       | User-defined channel identification, such as wx/qq, etc. |
| info      | no       | Additional login user information, customizable          |

![The contents of the 3 parameters will be correspondingly stored in the column of the exported data](https://gblobscdn.gitbook.com/assets%2F-Lnu1UZ4dgrL0WcgooHk%2F-M8xZPotFdHz1N16Lc8D%2F-M8x\_Ces9PS6wJu2iMhz%2Fimage.png?alt=media\&token=4885e15a-8fe4-467d-8087-f9ba0bbbbd7f)

**Comparison of examples of normal link and embedded link**

{% hint style="info" %}
\[Normal link]

https://in.survey.imur.tencent.com/?sid=5e8d767b76051f46707cf692

\[Embedded link]

&#x20;https://in.survey.imur.tencent.com/?**sid=5e8d767b76051f46707cf692\&openid=XXXX\&source=XXXX\&info=XXXX**
{% endhint %}



_\*For reference only_\
