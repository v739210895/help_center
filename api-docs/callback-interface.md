# Callback Interface

### Interface Description

#### Interface Definition

After the user submits the questionnaire, the questionnaire system will call back parameters such as the login status to the developer, which is suitable for scenarios such as reward distribution and status modification.

#### Scenarios

After the user submits the questionnaire, the questionnaire system will call back parameters such as the login status to the developer, which is suitable for scenarios such as reward distribution and status modification.Note that this callback action is completed asynchronously by the questionnaire server, and there will be a second delay.

The configuration of the login status callback interface is turned on under \[Settings] -> \[Login status callback interface] under questionnaire editing, and the user needs to configure the \[key] and \[callback address], and perform signature verification on the request parameters in the \[callback address],to prevent the malicious attack to the interface.

{% hint style="info" %}
Support public network callback and intranet L5 callback

1. The callback address starts with http:// or https://
2. Support L5 address, such as: http://12345601:987654/surveytest1
{% endhint %}



### Sign Signature Algorithm

#### Algorithm flow

1. Provide necessary parameters (see API interface for details), and kv data structure;
2. Add appSecret as the signature key field to the kv data structure;
3. Sort the keys in ascii ascending order;
4.  Traverse the sorted kv data structure, and concatenate all elements into a string according to the

    pattern of "key1value1key2value2";
5. Carry out md5 summary on the spliced database to get the sign signature;
6. Compare the received sign with the sign signature calculated in step 5;
7. Return the status code.

{% hint style="info" %}
1. appSecret of Code example is the signature key, which is the same as the callback address, and is configured on the "Settings" page of the questionnaire. 
2. Example of the spliced encrypted string _appSecretuIVtlG06callback_paramscallbackparamsinfotestinfosid5fe4428376051f85cc5f 3_973timestamp1609408137uidtestuseruid_sourcetestsourceuser_typeweak_third_party

\[Note] 

The calculation of signatures cover the default parameters and appSecret. The default parameters with empty values and other unspecified parameters are excluded.
{% endhint %}

_Code example_

PHP code

```php
<?php
$query = $_GET;

$appSecret = 'iamsecret';

$sign = $query['sign'];
unset($query['sign']);

// add signature key
$params = array_merge($query, [
    'appSecret' => $appSecret,
]);

ksort($params);

$str = '';
foreach ($params as $key => $value) {
    $str .= $key.$value;
}

$mySign = strtolower(md5($str));

echo json_encode([
    'status' => ($mySign === $sign) ? 'ok' : 'failed',
]);
```

_Callback URL example_

```
Developer callback url?sid=5da414769e8aa80019305e32&timestamp=1573556685&uid=test_user&user_type=third_party&uid_source=qq&info=afdadsfasdfasdf&callback_params=callbackparams&sign=38408d6222e1a4c6fa598e4820443ca8
```

 

## Callback parameter description

### Parameter Description

The callback interface uses GET request.

| parameter       | Must pass | Whether to participate in encryption | type   | Limit length | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------- | --------- | ------------------------------------ | ------ | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| sid             | Yes       | Yes                                  | string | 32           | Questionnaire id                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| uid             | no        | Yes                                  | string | 255          | It is only passed when the questionnaire needs to log in, the unique ID of the logged-in user (eg, the player openid in the MSDK login verification / the uid passed in in the strict verification mode / the openid passed in in the nonverification mode)                                                                                                                                                                                                          |
| user_type       | no        | Yes                                  | string | 2-10         | It is only passed when the questionnaire needs to be logged in. The type of logged-in user, including the values of: _Wechat_, _QQ_ , _MSDK (in-game)_, _third_party (parameter transmission-strict verification mode)_, _weak_third_party (parameter transmission-no verification mode)_                                                                                                                                                                            |
| uid_source      | no        | Yes                                  | string | 2-10         | It is only passed when the questionnaire needs to be logged in. The source of the logged-in user, currently only has the values wx and qq under msdk, and the non-MSDK login status transfer needs to be defined by the developer.                                                                                                                                                                                                                                   |
| timestamp       | Yes       | Yes                                  | int    | 10           | Timestamp                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| sign            | Yes       | no                                   | string | 32           | Signature, refer to signature algorithm                                                                                                                                                                                                                                                                                                                                                                                                                              |
| callback_params | no        | Yes                                  | string | 255          | <p>The developer customizes the callback parameters, and the business side needs additional parameters to be used. </p><p>【Note】</p><p>1. This parameter is transparently transmitted from the client to the developer server through the questionnaire link, for example: https: //in.survey.imur.tencent.com/ sid=xxx&#x26;?callback_params=xxxxx </p><p>2. If the value is encoded during the transparently transmitted , it must be decoded when encrypting.</p> |
| info            | no        | Yes                                  | string | 255          | It is additional information of the logged-in user. This field needs to be used with  [parameter transfer (no verification)](parameter-transfer-interface-no-verification-mode.md) ; if you use MSDK v3/v5, INTL automatic login, _info_ is a normal parameter during the transparently transmitted and does not participate in encryption.                                                                                                                          |

1. The optional parameters participate in encryption when it has a value, otherwise it will not.
2. Unspecified parameters are not involved in encryption, please refer to: [Why do I receive callback parameters that are not specified in the document?](callback-interface.md#why-do-i-receive-callback-parameters-that-are-not-specified-in-the-document)
3. If you use MSDK v3/v5, INTL to log in automatically, _info_ is only transparently transmitted as a common parameter, and does not participate in encryption, nor is it collected in the answer.



### Callback success agreement return format

After the developer receives the callback and processes the business process normally, it must return the

following specified json format to the questionnaire server:

```
{
"status" : "ok"
}
```

### Callback business code

If the business side needs to make some specific identification in the callback, you can pass the business_code field, and the questionnaire system will store the value of this field in es, which can be used to filter data based on the identification in the open interface. The business_code value range must be -32768 \~ 32767, if it exceeds this range, it will not be stored. Example:

```
{
"status" : "ok",
"business_code" : 1000
}
```

{% hint style="info" %}
1. business_code must be of type int16, ie -32768 \~ 32767
2. The callback business code will only be written when the status is ok
{% endhint %}

### The same questionnaire supports multiple callback addresses

The **client** adds the callback parameter into the questionnaire link to distinguish which callback address is called back after the submission. Up to 10 callback addresses can be configured, and the specific callback address is actually specified by the client.

**Note: **Each time you submit a questionnaire, it can only call back to one address. If the questionnaire link does not contain the _callback_, it will call back to address 1 by default.

{% hint style="info" %}
If the value of _callback_  is 2, the system will callback the login status information to the callback address 2 after submission

[https://in.weisurvey.com/?sid=5f87b81376051f331039dfe5\&openid={openid}](https://in.weisurvey.com/?sid=5f87b81376051f331039dfe5\&openid={openid}) \&callback=2
{% endhint %}

![Multiple callback address configuration](<../.gitbook/assets/image (689).png>)

## Callback interface debugging tool 

You can use the callback interface debugging tool (it is recommended to use chrome to open) to confirm the callback and signature verification.

![Callback interface debugging tool](<../.gitbook/assets/image (691).png>)

## Common problem

### Why can't I receive callback messages?

Under the condition that the provided callback address is correct, please check the following items:

1. **Whether the callback address is publicly accessible**: If not, please use the internal network L5 callback address or change _callback address_ to publicly accessible.
2. **Whitelist restriction on the server**: If so, please contact the "IMUR Questionnaire System Assistant" on WeChat to obtain the questionnaire system export IP, and add it to the access whitelist (domestic/overseas environment is completely isolated, export IP is different, please distinguish according to needs Obtain)



### Why do I receive callback parameters that are not specified in the document?

This parameter is transparently transmitted from the client to the developer server through the questionnaire link, causing the developer server to receive callback parameters that are not described in the document. 

Common scenarios include:

* When logging in to MSDK, the browser will automatically add the player's login status information after the questionnaire link 
* The client might add custom parameters after the questionnaire link 
* In _parameter transfer (strict verification mode)_/_(non-verification mode_), login parameters such as player id are required to be added

{% hint style="info" %}
**Special Note:**

1. The optional parameters participate in encryption when it has a value, otherwise it will not.
2. Unspecified parameters are not involved in encryption, please refer to: [Why do I receive callback parameters that are not specified in the document?](callback-interface.md#why-do-i-receive-callback-parameters-that-are-not-specified-in-the-document)
3. If you use MSDK v3/v5, INTL to log in automatically, _info_ is only transparently transmitted as a common parameter, and does not participate in encryption, nor is it collected in the answer.
{% endhint %}

![](<../.gitbook/assets/image (692).png>)

****
