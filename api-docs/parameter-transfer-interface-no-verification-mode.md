# Parameter Transfer Interface \(Non-Verification Mode\)

### Interface Description

#### Interface definition <a id="jie-kou-ding-yi"></a>

The **parameter transfer interface \(non-verification mode\)** interface is used to  

\(1\) third-party developers have their own user id \(such as facebook id, Game user id, etc.\), but they want to send the login status to the questionnaire system;

\(2\) Non-standard access to MSDK, cannot collect openid with MSDK-V3 or MSDK-V5 .

####  <a id="jie-kou-shuo-ming-1"></a>

#### Interface Description <a id="jie-kou-shuo-ming-1"></a>

The developer dynamically splices the specified parameters into the questionnaire link, realizes the login state transfer and other parameter transfer, and stores them in the questionnaire system. The parameters include openid \(required\), source \(optional\), info \(optional\), respectively Stored in the uid, uidSource, and info columns in the exported data.

| Parameter | Required | Description |
| :--- | :--- | :--- |
| openid | Yes | The unique ID of the logged-in user |
| source | no | User-defined channel identification, such as wx/qq, etc. |
| info | no | Additional login user information, customizable |

![The contents of the 3 parameters will be correspondingly stored in the column of the exported data](https://gblobscdn.gitbook.com/assets%2F-Lnu1UZ4dgrL0WcgooHk%2F-M8xZPotFdHz1N16Lc8D%2F-M8x_Ces9PS6wJu2iMhz%2Fimage.png?alt=media&token=4885e15a-8fe4-467d-8087-f9ba0bbbbd7f)

**Comparison of examples of normal delivery links and embedded delivery links**

{% hint style="info" %}
\[Normal link\]

https://in.survey.imur.tencent.com/?sid=5e8d767b76051f46707cf692

\[Link processed\]

 https://in.survey.imur.tencent.com/?**sid=5e8d767b76051f46707cf692&openid=XXXX&source=XXXX&info=XXXX**
{% endhint %}



_\*The values ​​corresponding to the above parameters are for display only_  


