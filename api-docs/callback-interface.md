# Callback interface

### Interface Description

#### Interface Description

After the user submits the questionnaire, the questionnaire system will call back parameters such as the login status to the developer, which is suitable for scenarios such as reward distribution and status modification.

#### scenes to be used

After the user submits the questionnaire, the questionnaire system will call back parameters such as the login status to the developer, which is suitable for scenarios such as reward distribution and status modification.Note that this return action is completed asynchronously by the questionnaire server, and there will be a certain delay \( Second level\).

The configuration of the login state callback interface is turned on under \[Settings\] -&gt; \[Login state callback interface\] under questionnaire editing, and the user needs to configure the \[key\] and \[callback address\], and perform signature verification on the request parameters in the \[callback address\]. Prevent malicious interface brushing.

{% hint style="info" %}
Support public network callback and intranet L5 callback

1. The callback address starts with http:// or https://
2. Support L5 address, such as: [http://12345601:987654/surveytest1](http://12345601:987654/surveytest1)
{% endhint %}



### sign signature algorithm

#### Algorithm flow



