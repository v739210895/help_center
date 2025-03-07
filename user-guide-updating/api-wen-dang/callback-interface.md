# Callback Interface

### Interface Description

#### Interface Definition

After the user submits the survey, the survey system will call back parameters such as the login status to the developer, which is suitable for scenarios such as reward distribution and status modification.

#### Scenarios

After the user submits the survey, the survey system will call back parameters such as the login status to the developer, which is suitable for scenarios such as reward distribution and status modification.Note that this callback action is completed asynchronously by the survey server, and there will be a second delay.

The configuration of the login status callback interface is turned on under \[Settings] -> \[Login status callback interface] under survey editing, and the user needs to configure the \[key] and \[callback address], and perform signature verification on the request parameters in the \[callback address],to prevent the malicious attack to the interface.

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
1) appSecret of Code example is the signature key, which is the same as the callback address, and is configured on the "Settings" page of the questionnaire.&#x20;
2) Example of the spliced encrypted string _appSecretuIVtlG06callback\_paramscallbackparamsinfotestinfosid5fe4428376051f85cc5f &#x33;_&#x39;73timestamp1609408137uidtestuseruid\_sourcetestsourceuser\_typeweak\_third\_party

\[Note]&#x20;

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



Golang code

```go
import (
	"sort"
)

func VerifySign(sign string, params map[string]string, secret string) bool {
	return sign == MakeSign(params, secret)
}

func MakeSign(data map[string]string, secret string) string {
	str := MakeSignParamStr(data, secret)

	sign := MD5(str)

	return sign
}

func MakeSignParamStr(data map[string]string, secret string) string {
	data["appSecret"] = secret

	var keys = make([]string, 0)
	for key := range data {
		keys = append(keys, key)
	}
	sort.Strings(keys)

	str := ""
	for _, sortKey := range keys {
		if data[sortKey] != "" {
			str = str + sortKey + data[sortKey]
		}
	}
	delete(data, "appSecret")

	return str
}

```

C# code, full example

```csharp
using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Security.Cryptography;
using System.Text;
using System.Web;

namespace TxProxy.Services;

public static class Program
{
	public static void Main()
	{
		var queryString = ""; // important! Your queryString

		var request = HttpUtility.ParseQueryString(queryString);
		var requestDict = request.AllKeys.ToDictionary(k => k!, k => request[k]);
		var sign = requestDict["sign"]!;
		var verifier = new PollCallbackAppSecretVerifier(""); // important! Your survey appSecret
		var isVerified = verifier.Verify(sign, requestDict);

		Console.WriteLine("Verification result: " + (isVerified ? "Valid" : "Invalid"));
	}
}

public sealed class PollCallbackAppSecretVerifier
{
    private static readonly string[] EncryptList =
    {
        "sid",
        "uid",
        "user_type",
        "uid_source",
        "timestamp",
        "callback_params",
	"info",
    };

    private readonly string appSecret;

    public PollCallbackAppSecretVerifier(string appSecret)
    {
        this.appSecret = appSecret;
    }

    // Sign signature algorithm flow
    public bool Verify(string sign, Dictionary<string, string> queryParams)
	{
		var verifyParams = EncryptList.ToHashSet();

		var pairs = queryParams
			.Where(data => verifyParams.Contains(data.Key))
			.Append(new KeyValuePair<string, string>("appSecret", this.appSecret))
			.ToList();

		var sortedPairs = pairs.OrderBy(pair => pair.Key);

		var signBytes = Convert.FromHexString(sign);

		var sb = new StringBuilder();
		foreach (var (k, v) in sortedPairs)
		{
			sb.Append(k);
			sb.Append(v);
		}

		var serialized = sb.ToString();

	#pragma warning disable CA5351
		var result = MD5.HashData(Encoding.ASCII.GetBytes(serialized));
	#pragma warning restore CA5351

		return StructuralComparisons.StructuralEqualityComparer.Equals(result, signBytes);
	}
}

```

_Callback URL example_

```
Developer callback url?sid=5da414769e8aa80019305e32&timestamp=1573556685&uid=test_user&user_type=third_party&uid_source=qq&info=afdadsfasdfasdf&callback_params=callbackparams&sign=38408d6222e1a4c6fa598e4820443ca8
```

&#x20;

## Callback parameter description

### Parameter Description

The callback interface uses GET request.

<table data-header-hidden><thead><tr><th width="150">parameter</th><th width="150">Required</th><th width="150">Whether to participate in encryption</th><th width="150">type</th><th width="150">Limit length</th><th width="556">Description</th></tr></thead><tbody><tr><td>parameter</td><td>Response parameters</td><td>Whether to participate in encryption</td><td>type</td><td>Limit length</td><td>Description</td></tr><tr><td>sid</td><td>Yes</td><td>Yes</td><td>string</td><td>32</td><td>Questionnaire ID</td></tr><tr><td>uid</td><td>no</td><td>Yes</td><td>string</td><td>255</td><td>It is only passed when the questionnaire needs to log in, the unique ID of the logged-in user (eg, the player openid in the MSDK login verification / the uid passed in in the strict verification mode / the openid passed in in the nonverification mode)</td></tr><tr><td>user_type</td><td>no</td><td>Yes</td><td>string</td><td>2-10</td><td>It is only passed when the questionnaire needs to be logged in. The type of logged-in user, including the values of: <em>Wechat</em>, <em>QQ</em> , <em>MSDK (in-game)</em>, <em>third_party (parameter transmission-strict verification mode)</em>, <em>weak_third_party (parameter transmission-no verification mode)</em></td></tr><tr><td>uid_source</td><td>no</td><td>Yes</td><td>string</td><td>2-10</td><td>It is only passed when the questionnaire needs to be logged in. The source of the logged-in user, currently only has the values wx and qq under msdk, and the non-MSDK login status transfer needs to be defined by the developer.</td></tr><tr><td>timestamp</td><td>Yes</td><td>Yes</td><td>int</td><td>10</td><td>Timestamp</td></tr><tr><td>sign</td><td>Yes</td><td>no</td><td>string</td><td>32</td><td>Signature, refer to signature algorithm</td></tr><tr><td>callback_params</td><td>no</td><td>Yes</td><td>string</td><td>255</td><td><p>The developer customizes the callback parameters, and the business side needs additional parameters to be used. </p><p>【Note】</p><p>1. This parameter is transparently transmitted from the client to the developer server through the questionnaire link, for example: https: //in.survey.imur.tencent.com/ sid=xxx&#x26;?callback_params=xxxxx </p><p>2. If the value is encoded during the transparently transmitted , it must be decoded when encrypting.</p></td></tr><tr><td>info</td><td>no</td><td>Yes</td><td>string</td><td>255</td><td>It is additional information of the logged-in user. This field needs to be used with  <a href="parameter-transfer-interface-no-verification-mode.md">parameter transfer (no verification)</a> ; </td></tr><tr><td>effective</td><td>Yes</td><td>no</td><td>bool</td><td>4-5</td><td></td></tr><tr><td>aid</td><td>Yes</td><td>no</td><td>string</td><td>32</td><td>Answer ID</td></tr></tbody></table>

1. The optional parameters participate in encryption when it has a value, otherwise it will not.
2. Unspecified parameters are not involved in encryption, please refer to: [Why do I receive callback parameters that are not specified in the document?](callback-interface.md#why-do-i-receive-callback-parameters-that-are-not-specified-in-the-document)





### Callback success agreement return format

After the developer receives the callback and processes the business process normally, it must return the

following specified json format to the questionnaire server:

```json
{
    "status" : "ok"
}
```

### Callback business code

If the business side needs to make some specific identification in the callback, you can pass the business\_code field, and the questionnaire system will store the value of this field in es, which can be used to filter data based on the identification in the open interface. The business\_code value range must be -32768 \~ 32767, if it exceeds this range, it will not be stored. Example:

```json
{
    "status" : "ok",
    "business_code" : 1000
}
```

{% hint style="info" %}
1. business\_code must be of type int16, ie -32768 \~ 32767
2. The callback business code will only be written when the status is ok
{% endhint %}

### The same questionnaire supports multiple callback addresses

The **client** adds the callback parameter into the questionnaire link to distinguish which callback address is called back after the submission. Up to 10 callback addresses can be configured, and the specific callback address is actually specified by the client.

**Note:** Each time you submit a questionnaire, it can only call back to one address. If the questionnaire link does not contain the _callback_, it will call back to address 1 by default.

{% hint style="info" %}
If the value of _callback_  is 2, the system will callback the login status information to the callback address 2 after submission

[https://in.weisurvey.com/?sid=5f87b81376051f331039dfe5\&openid={openid}](https://in.weisurvey.com/?sid=5f87b81376051f331039dfe5\&openid={openid}) \&callback=2
{% endhint %}

![Multiple callback address configuration](../../.gitbook/assets/回调.png)

## Callback interface debugging tool&#x20;

You can use the callback interface debugging tool (it is recommended to use chrome to open) to confirm the callback and signature verification.

[https://test.a.imur.tencent.com/static/tools-out/#/callback](https://test.a.imur.tencent.com/static/tools-out/#/callback)

![Callback interface debugging tool](<../../.gitbook/assets/image (340).png>)

## Common problem

### Why can't I receive callback messages?

Under the condition that the provided callback address is correct, please check the following items:

1. **Whether the callback address is publicly accessible**: If not, please use the internal network L5 callback address or change _callback address_ to publicly accessible.
2. **Whitelist restriction on the server**: If so, please contact the "IMUR Questionnaire System Assistant" on WeChat to obtain the questionnaire system export IP, and add it to the access whitelist (domestic/overseas environment is completely isolated, export IP is different, please distinguish according to needs Obtain)



### Why do I receive callback parameters that are not specified in the document?

This parameter is transparently transmitted from the client to the developer server through the questionnaire link, causing the developer server to receive callback parameters that are not described in the document.&#x20;

Common scenarios include:

* When logging in to MSDK, the browser will automatically add the player's login status information after the questionnaire link&#x20;
* The client might add custom parameters after the questionnaire link&#x20;
* In _parameter transfer (strict verification mode)_/_(non-verification mode_), login parameters such as player id are required to be added

{% hint style="info" %}
**Special Note:**

1. The optional parameters participate in encryption when it has a value, otherwise it will not.
2. Unspecified parameters are not involved in encryption, please refer to: [Why do I receive callback parameters that are not specified in the document?](callback-interface.md#why-do-i-receive-callback-parameters-that-are-not-specified-in-the-document)
3. ~~If you use MSDK v3/v5, INTL to log in automatically, _info_ is only transparently transmitted as a common parameter, and does not participate in encryption, nor is it collected in the answer.~~**If you use intl/MSDK login, the latest version requires adding 'info' as a parameter in the signature.**
{% endhint %}
