# 开放接口

## 问卷开放接口

问卷系统作为调研工具，为了支持不同的业务场景，将问卷相关的接口进行开放。

### [接口调用方式](./#jie-kou-tiao-yong-fang-shi-1)

### [签名算法](./#qian-ming-suan-fa-1)

### [接口](./#jie-kou-1)

### [常见问题](./#chang-jian-wen-ti-1)

## 接口调用方式

接口调用使用`cl5`方式调用。

#### 国内环境

mod\_id: `65080257` cmd\_id: `65536`

调用时Header中必需带上Host，Host值为`survey.imur.oa.com`。

#### 海外环境

mod\_id: `65080257` cmd\_id: `131072`

调用时Header中必需带上Host，Host值为`outsurvey.imur.oa.com`。

## 签名算法

开放接口采用参数+密钥的方式生成接口签名sign，密钥由管理端进行配置，每份问卷可配置独立的密钥，保证数据安全性；密钥可在问卷编辑页选择【设置】-&gt; 【API调用】中配置。

**注意**签名会对timestamp进行校验，生成超过10分钟的sign视为无效，需要重新生成。

#### 算法流程

1. 提供必要参数（详情需要根据每个接口要求的参数），使用kv数据结构；
2. 添加问卷ID参数sid到kv数据结构；
3. 添加当前时间戳参数timestamp到kv数据结构；
4. 添加appSecret作为签名密钥字段到kv数据结构；
5. 对key进行按ascii升序排序；
6. 遍历排序后的kv数据结构，把所有元素，按照“key1value1key2value2”的模式拼接成字符串；
7. 对拼接的数据库进行md5摘要，即可得sign签名；
8. 添加sign作为签名字段到kv数据结构；
9. 将kv数据结构转换成http的query请求参数；
10. 带上query请求参数调用登录态传递接口。

#### 代码示例

_PHP代码_ [Demo](open.demo.php)

```php
<?php
$appSecret = 'iamsecret';

$sid = '5dc5727a76051f14b96d5172';
$timestamp = time();

$query = [
    'sid' => $sid,
    'timestamp' => $timestamp,
];

// 添加密钥
$params = array_merge($query, [
    'appSecret' => $appSecret,
]);

ksort($params);

$str = '';
foreach ($params as $key => $value) {
    $str .= $key.$value;
}

$sign = strtolower(md5($str));

// IP从l5获取
$url = "http://9.84.189.40/open/v1/surveys/$sid?sign=$sign&timestamp=$timestamp";
```

## 接口

API接口采用RESTful方式实现，在接口地址中出现的sid为问卷的ID，具体的接口不再说明。

### 问卷编辑

#### **1、获取问卷详情**

获取问卷详情数据。

**接口地址**

```text
GET http://{host}/open/v1/surveys/{sid}
```

**参数说明**

无。

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

### 数据统计

#### **1、回收数据概述**

获取问卷的答题量、浏览量、答题平均时长。

**接口地址**

```text
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

#### **2、答题时长中位数**

获取问卷用户答题时长的中位数。

**接口地址**

```text
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

#### **3、答题时长分布**

获取问卷答题时长在时间上的分布情况。

**接口地址**

```text
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

#### **4、答题回收趋势**

获取问卷用户答题每日答题回收数据量趋势。

**接口地址**

```text
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

#### **5、各题型统计**

获取问卷各个题型的数据统计。当前接口返回的数据相对比较精简，没有问卷的内容，在使用时要配合获取问卷详情来使用。下面的接口返回示例会说明每个ID对应的题目类型。

**注意**当前联动题仅支持统计数。主观题使用主观题或选项填空题列表接口获得。

**接口地址**

```text
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

#### **6、主观题或选项填空题列表**

获取主观题/选项填空题列表，支持分页。

**接口地址**

```text
GET http://{host}/open/v1/statistics/{sid}/blanks
```

**参数说明**

使用GET请求方式传参。

| 参数 | 是否必须 | 数据类型 | 限制长度 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| blank\_id | 是 | string | 4 | 如果是主观题则为question_id；如果是选项中的填空题，由question\_id与option\_id组成，格式：{qid}_{oid} |
| page | 否 | int |  | 页码，起码为1，默认为1 |
| page\_size | 否 | int |  | 页数，默认为10 |

**返回数据**

```javascript
{
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



#### **7、答题数据列表**

获取用户答题数据列表，支持分页。

**接口地址**

```text
POST http://{host}/open/v1/answers/{sid}
```



| 参数 | 是否必须 | 数据类型 | 说明 |
| :--- | :--- | :--- | :--- |
| query | 否 | object | es筛选条件 |
| page | 否 | int | 页码，起码为1，默认为1 |
| page\_size | 否 | int | 页数，默认为10 |

#### **8、获取答题数据详情**

获取回调中的aid获取一条答题数据。

**接口地址**

```text
GET http://{host}/open/v1/answers/{sid}/{aid}
```



## 常见问题

