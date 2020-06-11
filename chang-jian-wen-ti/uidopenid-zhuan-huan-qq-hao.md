# uid\(openid\)转换QQ号

### openid是什么：应用内用户身份的唯一标识

openid是用户身份的唯一标识，用于区分单个用户。目前，基本所有的游戏或应用只能够获取到openid，无法直接获取到qq号或微信号。

每个应用都有一个appid，openid是QQ号或微信号结合appid加密后的结果。同一个QQ号或微信号，在不同的应用中对应不同的openid，可使用业务受理系统进行QQ号/微信号转openid的操作。

{% hint style="info" %}
#### QQ号/微信号转openid，使用业务受理系统：[http://ptzh.sap.cm.com/ajax/ajax.html](http://ptzh.sap.cm.com/ajax/ajax.html)
{% endhint %}

![&#x540C;&#x4E00;QQ&#x53F7;&#xFF0C;&#x4E0D;&#x540C;&#x5E94;&#x7528;&#x4E2D;&#xFF0C;openid&#x4E0D;&#x4E00;&#x6837;](../.gitbook/assets/image%20%28496%29.png)

![&#x4E1A;&#x52A1;&#x53D7;&#x7406;&#x7CFB;&#x7EDF;&#x53EF;&#x4EE5;&#x8FDB;&#x884C;QQ&#x53F7;/&#x5FAE;&#x4FE1;&#x53F7;&#x8F6C;openid&#x7684;&#x64CD;&#x4F5C;](../.gitbook/assets/image%20%28492%29.png)

### 如何将openid转化为QQ号：在统一登录平台上提交转换任务

{% hint style="info" %}
#### openid转QQ号，使用统一登录平台：[http://qqlogin.oa.com/open\_uin.php?type=1](http://qqlogin.oa.com/open_uin.php?type=1)

#### 新版问卷系统APPid：101788602     旧版问卷系统Appid：101481019

#### 其他系统的Appid查询：[http://ptzh.sap.cm.com/ajax/ajax.html](http://ptzh.sap.cm.com/ajax/ajax.html)
{% endhint %}

![&#x7528;&#x6237;&#x7684;openid&#x5B58;&#x50A8;&#x5728;uid&#x4E00;&#x5217;&#xFF0C;uid&#x8868;&#x793A;&#x4E3A;userId](../.gitbook/assets/image%20%28497%29.png)

![&#x7EDF;&#x4E00;&#x767B;&#x5F55;&#x5E73;&#x53F0;&#x64CD;&#x4F5C;&#x6307;&#x5F15;](../.gitbook/assets/image%20%28494%29.png)

