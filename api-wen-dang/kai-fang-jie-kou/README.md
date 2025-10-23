# 开放接口（管理端）

## 简介

为支持各类业务场景，将问卷相关的接口进行开放。第三方可通过接口的形式查询问卷内容（题目&选项）、回收统计、指定的答卷数据。

1\. [接口调用方式](./#1.-jie-kou-tiao-yong-fang-shi)

2\. [签名算法](./#2.-qian-ming-suan-fa)

3\. [问卷内容接口](./#3.-wen-juan-nei-rong-jie-kou)

4\. [回收概况接口](./#4-hui-shou-gai-kuang-jie-kou)

5\. [数据统计接口](./#5-da-ti-shu-ju-tong-ji)

6\. [答题数据详情接口](./#5-da-ti-shu-ju-xiang-qing-jie-kou)

7\. [常见问题](./#4.-chang-jian-wen-ti)

## 1. 接口调用方式

#### 国内环境

【cl5/北极星方式】

旧cl5: mod\_id: `65080257` cmd\_id: `65536`

北极星: \`65080257:65536\`

【通用方式】

{host}为`survey.imur.tencent.com`

#### 海外环境

【通用方式】{host}为`www.outweisurvey.com`

## 2. 签名算法

### 2.1 签名算法V1版本(不推荐)

开放接口采用参数+密钥的方式生成接口签名sign，密钥由管理端进行配置，每份问卷可配置独立的密钥，保证数据安全性；密钥需在问卷编辑页选择【设置】-> 【API调用】中配置。

**注意：**&#x7B7E;名会对timestamp进行校验，生成超过10分钟的sign视为无效，需要重新生成。

#### 2.1.1 算法流程

1. 提供必要参数（详情需要根据每个接口要求的参数），使用kv数据结构；
2. 添加问卷ID参数 sid 到kv数据结构；
3. 添加当前时间戳参数timestamp到kv数据结构；
4. 添加appSecret作为签名密钥字段到kv数据结构；
5. 对key进行按ascii升序排序；
6. 遍历排序后的kv数据结构，把所有元素，按照“key1value1key2value2”的模式拼接成字符串；
7. 对拼接的数据库进行md5摘要，即可得sign签名；
8. 添加sign作为签名字段到kv数据结构；
9. 将kv数据结构转换成http的query请求参数；
10. 带上query请求参数调用登录态传递接口。

{% hint style="info" %}
【注】appSecret即查询密钥，在问卷的“设置”页配置。配置方法详见[API调用配置](../../cao-zuo-zhi-yin/wen-juan-she-zhi/chuan-can-tiao-zhuan-hui-tiao.md#api-tiao-yong)
{% endhint %}

#### 2.1.2 代码示例

```php
class Sign
{
    /**
     * 除去数组中的空值和签名参数、然后排序、然后生成md5签名
     * @param array $params 签名参数组
     * @param $appKey appKey
     * @param $appSecret 签名密钥
     * @param $timestamp 时间戳
     * @return array 去掉空值与签名参数后并排序的新签名参数组
     */
    public static function generateSign($params, $appKey, $appSecret, $timestamp)
    {
        $params = array_merge($params, compact('appKey', 'appSecret', 'timestamp'));
        $params = self::paramsFilter($params); // 去空
        $params = self::argSort($params); // 排序
        $preSign = self::generateStr($params); // 拼接
        return strtolower(md5($preSign));
    }

    /**
     * 检测签名是否匹配
     * @param $sign 接受到的签名
     * @param array $params 签名参数组
     * @param $appKey appKey
     * @param $appSecret 签名密钥
     * @param $timestamp 时间戳
     * @return boolean
     */
    public static function verifySign($sign, $params, $appKey, $appSecret, $timestamp)
    {
        $gsign = self::generateSign($params, $appKey, $appSecret, $timestamp);
        return ($gsign === $sign);
    }

    /**
     * 除去数组中的空值和签名参数
     * @param array $params 签名参数组
     * @return array 去掉空值与签名参数后的新签名参数组
     */
    public static function paramsFilter($params)
    {
        $paramsFilter = array();

        foreach ($params as $key => $value) {

            if (is_array($value) && !empty($value)) {
                $value = json_encode($value);
            }

            if ($key == "sign" || $key == "sign_type" || self::checkEmpty($value) === true) {
                continue;
            } else {
                $paramsFilter[$key] = $params[$key];
            }
        }
        return $paramsFilter;
    }

    /**
     * 检测值是否为空
     * @param    string $value 待检测的值
     * @return   boolean  null | "" | unsset 返回 true;
     */
    protected static function checkEmpty($value)
    {
        if (!isset($value)) {
            return true;
        }

        if ($value === null) {
            return true;
        }

        if (trim($value) === "") {
            return true;
        }

        return false;
    }

    /**
     * 对数组排序
     * @param array $params 排序前的数组
     * @return array 排序后的数组
     */
    public static function argSort($params)
    {
        ksort($params);
        reset($params);
        return $params;
    }

    /**
     * 方法2：把数组所有元素，按照“key1value1key2value2”的模式拼接成字符串
     * @param array $params 需要拼接的一维数组
     * @return string
     */
    public static function generateStr($params)
    {
        $arg = "";
        foreach ($params as $key => $value) {
            if (is_array($value) && !empty($value)) {
                $value = json_encode($value);
            }
            $arg .= $key . $value;
        }
        //如果存在转义字符，那么去掉转义
        if (get_magic_quotes_gpc()) {$arg = stripslashes($arg);}

        return $arg;
    }

}
```

### 2.2 签名算法V2 版本(推荐)

#### 2.2.1 算法流程

1. 提供指定参数：sid(问卷 ID)、timestamp(当前毫秒时间戳)、algorithm\_version(签名算法版本，使用 "v2")，并且使用kv数据结构；
2. 对key进行按ascii升序排序；
3. 遍历排序后的kv数据结构，把所有元素，按照“key1value1key2value2”的模式拼接成字符串；
4. 对拼接的数据库进行md5摘要，即可得sign签名；
5. 添加sign作为签名字段到kv数据结构；
6. 添加appSecret作为签名密钥字段到kv数据结构；
7. 将kv数据结构转换成http的query/body 的请求参数；
8. 带上请求参数调用登录态传递接口。

#### 2.2.2 代码示例

```go
query = make(map[string]string)
query["sid"] = "6718c32fa102ea95d00b2372"
query["algorithm_version"] = "v2"
query["timestamp"] = "1730442215"

sign := MakeSign(query, "xxx")

// MakeSign 生成签名
func MakeSign(data map[string]string, secret string) string {
	str := MakeSignParamStr(data, secret)

	sign := MD5(str)

	return sign
}

// MakeSignParamStr 生成参数串
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



## 3. 问卷内容接口

API接口采用RESTful方式实现，在接口地址中出现的sid为问卷的ID，具体的接口不再说明。

### **3.1 获取问卷详情**

获取问卷详情数据。

**接口地址**

```
GET http://{host}/open/v1/surveys/{sid}
```

**参数说明**

详见“返回数据”

**返回数据**

```javascript
{
    "data": {
        // ID
        "_id": "5e0b2ddc76051f02a521b297",
        // 更新时间
        "updated_at": "2019-12-31 19:16:52",
        // 创建时间
        "created_at": "2019-12-31 19:15:40",
        // 状态：null/0:未发布 1:已发布 2:未审核 3:已关闭
        "status": null,
        // 结束语
        "conclusion": "<p>bye</p>",
        // 配置
        "configs": {
            "showSerial": true,
            "language": "zh-CHS",
            "openApi": true,
            "apiSecret": "iamsecret"
        },
        // 欢迎语
        "introduction": "<p>hi</p>",
        // 分页
        "pages": [
            {
                "id": "RWT0",
                "questions": [
                    "UNE1",
                    "EVD4",
                    "MKV7",
                    "AIIa",
                    "NWNb",
                    "DPYc",
                    "VXUh",
                    "YVPm"
                ]
            },
            {
                "id": "LASn",
                "questions": [
                    "SHPo"
                ]
            }
        ],
        // 问题kv格式
        "questions": {
            // 单选题
            "UNE1": {
                "id": "UNE1",
                "type": "radio",
                "title": "单选题",
                "description": null,
                "relateBy": null,
                "relateCondition": "selected",
                "relateFor": [],
                // 单选题选项
                "options": [
                    {
                        "id": "YSO2",
                        "text": "选项1",
                        "blank": true,
                        "blankRequired": true
                    },
                    {
                        "id": "GFD3",
                        "text": "选项2"
                    }
                ],
                "required": true,
                "blank": false,
                "preLineNum": 1,
                "random": false,
                "randomReverse": false,
                "lastOptionFixed": false,
                "randomGroup": false,
                "randomGroupSetting": {
                    "random": false
                }
            },
            // 下拉题
            "EVD4": {
                "id": "EVD4",
                "type": "select",
                "title": "下拉题",
                "description": null,
                "relateBy": null,
                "relateCondition": "selected",
                "relateFor": [],
                // 下拉题选项
                "options": [
                    {
                        "id": "MVQ5",
                        "text": "选项1"
                    },
                    {
                        "id": "NQU6",
                        "text": "选项2"
                    }
                ],
                "required": true,
                "blank": false,
                "preLineNum": 1,
                "random": false,
                "randomReverse": false,
                "lastOptionFixed": false,
                "randomGroup": false,
                "randomGroupSetting": {
                    "random": false
                }
            },
            // 多选题
            "MKV7": {
                "id": "MKV7",
                "type": "checkbox",
                "title": "多选题",
                "description": null,
                "relateBy": null,
                "relateCondition": "selected",
                "relateFor": [],
                // 多选题选项
                "options": [
                    {
                        "id": "YKG8",
                        "text": "选项1"
                    },
                    {
                        "id": "LZG9",
                        "text": "选项2"
                    }
                ],
                "required": true,
                "blank": false,
                "preLineNum": 1,
                "random": false,
                "randomReverse": false,
                "lastOptionFixed": false,
                "randomGroup": false,
                "randomGroupSetting": {
                    "random": false
                },
                "optionalMin": -1,
                "optionalMax": -1,
                "exclusive": false
            },
            // 主观题
            "AIIa": {
                "id": "AIIa",
                "type": "subjective",
                "title": "主观题",
                "description": null,
                "required": true,
                "inputSize": "small",
                "inputRule": "any",
                "inputMin": 0,
                "inputMax": 0
            },
            // 量表题
            "NWNb": {
                "id": "NWNb",
                "type": "range",
                "title": "量表题",
                "description": null,
                "relateBy": null,
                "relateCondition": "selected",
                "relateFor": [],
                "required": true,
                // 最小值
                "minValue": 1,
                // 最大值
                "maxValue": 5,
                "tipsText": [
                    "不满意",
                    "一般",
                    "满意"
                ],
                "randomReverse": false,
                "fractionReverse": false
            },
            // 矩阵单选题
            "DPYc": {
                "id": "DPYc",
                "type": "matrixRadio",
                "title": "矩阵单选题",
                "description": null,
                "relateBy": null,
                "questionRelateBy": null,
                "relateCondition": "selected",
                "questionRelateCondition": "selected",
                // 标题
                "subTitles": [
                    {
                        "id": "OEDd",
                        "text": "问题a"
                    },
                    {
                        "id": "RUCe",
                        "text": "问题b"
                    }
                ],
                // 选项
                "options": [
                    {
                        "id": "RRGf",
                        "text": "选项1"
                    },
                    {
                        "id": "SXWg",
                        "text": "选项2"
                    }
                ],
                "required": true,
                "blank": false,
                "random": false,
                "questionRandom": false,
                "randomReverse": false,
                "questionRandomReverse": false,
                "lastOptionFixed": false,
                "questionLastOptionFixed": false
            },
            // 联动题
            "VXUh": {
                "id": "VXUh",
                "type": "cascade",
                "title": "联动题",
                "description": null,
                "subTitles": [
                    {
                        "id": "LGJi",
                        "text": "请选择"
                    },
                    {
                        "id": "ZNJj",
                        "text": "请选择"
                    }
                ],
                "options": [
                    {
                        "id": "TCDk",
                        "name": "选项1",
                        "children": [
                            {
                                "id": "EVRl",
                                "name": "选项1-1"
                            }
                        ]
                    }
                ],
                "required": true
            },
            // 信息栏
            "YVPm": {
                "id": "YVPm",
                "type": "information",
                "title": "信息栏"
            },
            "SHPo": {
                "id": "SHPo",
                "type": "radio",
                "title": "单选题",
                "description": null,
                "relateBy": null,
                "relateCondition": "selected",
                "relateFor": [],
                "options": [
                    {
                        "id": "YDZp",
                        "text": "选项1"
                    },
                    {
                        "id": "VIVq",
                        "text": "选项2"
                    }
                ],
                "required": true,
                "blank": false,
                "preLineNum": 1,
                "random": false,
                "randomReverse": false,
                "lastOptionFixed": false,
                "randomGroup": false,
                "randomGroupSetting": {
                    "random": false
                }
            }
        },
        // ID生成器种子
        "seed": 27,
        // 问卷标题
        "title": "<p>问卷标题</p>",
        "config": {
            "survey_id": "5e0b2ddc76051f02a521b297",
            "recovery_total": 0
        }
    }
}
```

**题型（type）有效值说明**

| type           | 题型      |
| -------------- | ------- |
| radio          | 单选题     |
| checkbox       | 多选题     |
| select         | 下拉题     |
| subjective     | 主观题     |
| range          | 量表题     |
| matrixRadio    | 矩阵单选题   |
| matrixCheckbox | 矩阵多选题   |
| matrixRange    | 矩阵量表题   |
| cascade        | 联动题     |
| attachment     | 附件上传题   |
| sort           | 排序题     |
| weight         | 权重分配题   |
| heatmap'       | 热力图题    |
| bipolar        | 文本拖拽题   |
| dragAndDrop    | 两级题     |
| maxDiff        | MaxDiff |
| conjoint       | 联合分析    |



## 4 回收概况接口

### **4.1 回收数据概述**

获取问卷的答题量、浏览量、答题平均时长。

**接口地址**

```
GET http://{host}/open/v1/statistics/{sid}/overview
```

**参数说明**

无。

**返回数据**

```javascript
{
    "data": {
        // 答题量
        "answers_count": 18,
        // 答题平均时长，单位：秒
        "avg_answer_consumed": 5469697.166666667,
        // 浏览量
        "pv_count": 1
    }
}
```

### **4.2 答题时长中位数**

获取问卷用户答题时长的中位数。

**接口地址**

```
GET http://{host}/open/v1/statistics/{sid}/consumed_median
```

**参数说明**

无。

**返回数据**

```javascript
{
    // 时长中位数，单位：秒
    "data": 5692681
}
```

### **4.3 答题时长分布**

获取问卷答题时长在时间上的分布情况。

**接口地址**

```
GET http://{host}/open/v1/statistics/{sid}/consumed_ranges
```

**参数说明**

无。

**返回数据**

```javascript
{
    // 区间从小到大排序
    "data": [
        {
            "key": "*-60.0",
            "to": 60,
            // 该区间的分布数量
            "doc_count": 0
        },
        {
            "key": "60.0-120.0",
            "from": 60,
            "to": 120,
            "doc_count": 0
        },
        {
            "key": "120.0-180.0",
            "from": 120,
            "to": 180,
            "doc_count": 0
        },
        {
            "key": "180.0-240.0",
            "from": 180,
            "to": 240,
            "doc_count": 0
        },
        {
            "key": "240.0-300.0",
            "from": 240,
            "to": 300,
            "doc_count": 0
        },
        {
            "key": "300.0-360.0",
            "from": 300,
            "to": 360,
            "doc_count": 0
        },
        {
            "key": "360.0-420.0",
            "from": 360,
            "to": 420,
            "doc_count": 0
        },
        {
            "key": "420.0-480.0",
            "from": 420,
            "to": 480,
            "doc_count": 0
        },
        {
            "key": "480.0-540.0",
            "from": 480,
            "to": 540,
            "doc_count": 0
        },
        {
            "key": "540.0-600.0",
            "from": 540,
            "to": 600,
            "doc_count": 0
        },
        {
            "key": "600.0-*",
            "from": 600,
            "doc_count": 18
        }
    ]
}
```

### **4.3 答题回收趋势**

获取问卷用户答题每日答题回收数据量趋势。

**接口地址**

```
GET http://{host}/open/v1/statistics/{sid}/answers_date_histogram
```

**参数说明**

无。

**返回数据**

```javascript
{
    "data": {
        "2019-11-28": {
            "key_as_string": "2019-11-28",
            "key": 1574899200000,
            // 回收数据量
            "doc_count": 2
        },
        "2019-11-29": {
            "key_as_string": "2019-11-29",
            "key": 1574985600000,
            "doc_count": 2
        },
        "2019-11-30": {
            "key_as_string": "2019-11-30",
            "key": 1575072000000,
            "doc_count": 0
        },
        ...
    }
}
```

## **5** 数据统计接口

### **5.1 各题型统计结果**

获取问卷各个题型的数据统计。当前接口返回的数据相对比较精简，没有问卷的内容，在使用时要配合获取问卷详情来使用。下面的接口返回示例会说明每个ID对应的题目类型。

**注意**当前联动题仅支持统计数。主观题使用主观题或选项填空题列表接口获得。

**接口地址**

```
GET http://{host}/open/v1/statistics/{sid}/answers
```

**参数说明**

无。

**返回数据**

```javascript
{
    "data": {
        // 单选题/下拉题/多选题
        "UNE1": {
            // 选项1 答题数
            "GFD3": 9,
            // 选项2 答题数
            "YSO2": 1
        },
        // 单选题/下拉题/多选题 有效填答量
        "UNE1_valid_count": 10,

        // 矩阵单选题
        // 矩阵单选题-题目1，格式为{question_id}_{option_id}
        "DPYc_RUCe": {
            // 选项1 答题数
            "RRGf": 9,
            // 选项2 答题数
            "SXWg": 1
        },
        // 题目1有效填答量
        "DPYc_RUCe_valid_count": 10,
        // 矩阵单选题-题目2
        "DPYc_OEDd": {
            "RRGf": 8,
            "SXWg": 2
        },
        // 题目2有效填答量
        "DPYc_OEDd_valid_count": 10,

        // 量表题，格式为{question_id}_short，后面的_short是固定的
        "OKWx_short": {
            // 选项 答题数
            "1": 1,
            "2": 1,
            "3": 1,
            "4": 1
        },
        // 平均分数
        "OKWx_short_avg": 2.5,
        // 有效填答量
        "OKWx_short_valid_count": 4,

        // 级联题
        // 第一级下的各个选项的填答量
        "FQZt": {
            "FCLv": 5
        },
        // 第一级下有效填答量
        "FQZt_valid_count": 5,
        // 第二级下各个选项的填答量，各个级的格式为{level1_id}_{level2_id}_...
        "FQZt_XKGu": {
            "AIFw": 5
        },
        // 第二级下有效填答量
        "FQZt_XKGu_valid_count": 5,

        // 主观题，格式为{question_id}_text，后面的_text是固定的
        "AIIa_text_count": 10
    }
}
```

### **5.2 主观题或选项填空答案列表**

获取主观题/选项填空题列表，支持分页。

**接口地址**

```
GET http://{host}/open/v1/statistics/{sid}/blanks
```

**参数说明**

使用GET请求方式传参。

| 参数         | 是否必须 | 数据类型   | 限制长度 | 说明                                                                                 |
| ---------- | ---- | ------ | ---- | ---------------------------------------------------------------------------------- |
| blank\_id  | 是    | string | 4    | 如果是主观题则为questio&#x6E;_&#x69;d；如果是选项中的填空题，由question\_id与option\_id组成，格式：{qid}_{oid} |
| page       | 否    | int    |      | 页码，起码为1，默认为1                                                                       |
| page\_size | 否    | int    |      | 页数，默认为10                                                                           |

**返回数据**{

```javascript
    "data": {
        // 总数
        "total": 5,
        "list": [
            {
                "text": "哈哈，你知道不",
                "length": 7
            },
            {
                "text": "04",
                "length": 2
            }
        ]
    }
}
```

## 6 答题数据详情接口

### **6.1 答题数据列表（批量查询）**

获取用户答题数据列表，支持分页。

**接口地址**

```
POST http://{host}/open/v1/answers/{sid}
```

| 参数         | 是否必须 | 数据类型   | 说明           |
| ---------- | ---- | ------ | ------------ |
| query      | 否    | object | es筛选条件       |
| page       | 否    | int    | 页码，起码为1，默认为1 |
| page\_size | 否    | int    | 页数，默认为10     |

**返回数据**

[点击查看样例](da-ti-xiang-qing-can-shu-shuo-ming.md#da-ti-shu-ju-lie-biao-pi-liang-cha-xun)

{% hint style="info" %}
page、page\_size未传参的情况下，默认最多仅返回1\*10条答题数据。
{% endhint %}



### **6.2 获取答题数据详情（单条查询）**

根据回调返回的aid，请求获取**指定一条**答题数据。

**接口地址**

```
GET http://{host}/open/v1/answers/{sid}/{aid}
```

**返回数据**

[点击查看样例](da-ti-xiang-qing-can-shu-shuo-ming.md#huo-qu-da-ti-shu-ju-xiang-qing-dan-tiao-cha-xun)



### **6.3 滚动获取答题数据列表**

滚动获取用户答题数据列表，可以通过 \`scroll\_id\` 获取检索大量的结果

**接口地址**

```
GET http://{host}/open/v1/scroll_answers/{sid}
```

| 参数         | 数据类型   | 说明                                                                     |
| ---------- | ------ | ---------------------------------------------------------------------- |
| scroll\_id | string | 列表中&#x7684;_&#x69;d字段(一般传入最后一个元素的_ \_i&#x64;_)，_&#x53EF;为空，为空时获取最早批的数据 |
| limit      | int    | 获取的条数，可为空，最大500                                                        |

**返回数据**

```json
{
    "data": [
        {"_id": "63214f991db57257716a5706", "xxx": "xxx"},
        {"_id": "63214f991db57257716a5707", "xxx": "xxx"}
    ]
}
```

### **6.4 获取id的哈希表**

获取问卷下所有id对应的文本和序号

**接口地址**

```
GET http://{host}/open/v1/surveys/{sid}/id_hash
```

**返回数据**

```json
{
    "data": {
        "LKM1": {
            "index": 1,
            "text": "这是一道单选题的标题"
        },
        "SWO2": {
            "index": 1,
            "text": "选项1"
        }
    }
}
```

## 7. 常见问题
