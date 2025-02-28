# 如何转换用户id(openid)与QQ号？

Step1：登入GACC系统后先申请权限，联系GACC助手通过申请openid转换为QQ号

openid转QQ号，使用统一登录平台：[https://qqlogin.woa.com/](https://qqlogin.woa.com/)

{% hint style="info" %}
问卷系统APPid：101788602    &#x20;

其他系统的Appid查询：[http://ptzh.sap.cm.com/ajax/ajax.html](http://ptzh.sap.cm.com/ajax/ajax.html)
{% endhint %}

![统一登录平台操作指引](<../../.gitbook/assets/image (290).png>)

## QQ号/微信号转openid

QQ号/微信号转openid，使用业务受理系统：[http://ptzh.sap.cm.com/ajax/ajax.html](http://ptzh.sap.cm.com/ajax/ajax.html)

![业务受理系统可以进行QQ号/微信号转openid的操作](<../../.gitbook/assets/image (16) (1) (1) (1) (1) (1) (1).png>)

### QQ号批量转换为gopenid

QQ号批量转换为gopenid（具备映射关系），使用GACC统一账号平台：[GACC 统一账号服务 (woa.com)](https://gacc.woa.com/)

咨询人：GACC助手

<figure><img src="../../.gitbook/assets/image (12) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Step1：登入GACC系统后先申请权限，联系GACC助手通过申请</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Step2：权限通过后按要求上传待转换的qq号文件</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Step3：通过平台离线任务，数据导出后有三列，分别为：QQ、openid、gopenid</p></figcaption></figure>

附录    openid是什么：应用内用户身份的唯一标识

openid是用户身份的唯一标识，用于区分单个用户。目前，基本所有的游戏或应用只能够获取到openid，无法直接获取到qq号或微信号。

每个应用都有一个appid，openid是QQ号或微信号结合appid加密后的结果。同一个QQ号或微信号，在不同的应用中对应不同的openid，可使用业务受理系统进行QQ号/微信号转openid的操作。

![同一QQ号，不同应用中，openid不一样](<../../.gitbook/assets/image (771).png>)
