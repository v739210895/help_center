# 开放接口（答题端）

### 简介

为支持各类业务场景，将问卷答题端相关的接口进行开放。第三方可通过接口的形式查询问卷内容（题目&选项）、提交答题数据等。

1. [问卷内容接口](kai-fang-jie-kou-da-ti-duan.md#huo-qu-wen-juan-nei-rong)
2. [提交答卷接口](kai-fang-jie-kou-da-ti-duan.md#2.-ti-jiao-da-juan-jie-kou)
3. [分段提交答卷接口](kai-fang-jie-kou-da-ti-duan.md#3.-fen-duan-ti-jiao-da-juan-jie-kou)
4. [问卷分发详情接口](kai-fang-jie-kou-da-ti-duan.md#4.-wen-juan-fen-fa-xiang-qing-jie-kou)
5. [media资源上传（单文件）](kai-fang-jie-kou-da-ti-duan.md#5.-media-zi-yuan-shang-chuan-dan-wen-jian)
6. [media资源上传（多文件）](kai-fang-jie-kou-da-ti-duan.md#6.-media-zi-yuan-shang-chuan-duo-wen-jian)
7. [ams领奖接口](kai-fang-jie-kou-da-ti-duan.md#7.-ams-ling-jiang-jie-kou)
8. [ams领奖状态查询接口](kai-fang-jie-kou-da-ti-duan.md#8.-ams-ling-jiang-zhuang-tai-cha-xun-jie-kou)
9. [获取用户答案接口](kai-fang-jie-kou-da-ti-duan.md#9.-huo-qu-yong-hu-da-an-jie-kou)

\-----------------------------------------------------------------------------------------------------



### 1.  问卷内容接口 <a href="#huo-qu-wen-juan-nei-rong" id="huo-qu-wen-juan-nei-rong"></a>

关联文档：[开放接口（管理端）--获取问卷详情](https://imur.gitbook.io/help_center/api-wen-dang/kai-fang-jie-kou#3.-wen-juan-nei-rong-jie-kou)

#### 接口地址 <a href="#a-oae-ae-ae-8" id="a-oae-ae-ae-8"></a>

```
正式地址： https://in.weisurvey.com/v2/api/
测试地址： 
Path： /surveys/:sid
Method： GET
```

**接口描述**

```
示例：
{
    "data": {
        "pages": [
            {
                "id": "0uCa",
                "questions": [
                    "11sj"
                ]
            }
        ],
        "questions": {
            "11sj": {
                "type": "radio",
                "title": "<p><strong>【单选题】</strong>您的职业？</p>",
                "desc": "<p>备注：<em><u>此处为</u></em><strong style="color: FFFF0000;"><em><u>备注信息</u></em></strong></p>",
                "required": true,
                "options": [
                    {
                        "text": "学生",
                        "id": "2Lrw"
                    },
                    {
                        "text": "教师",
                        "id": "3jhF"
                    },
                    {
                        "text": "公司职员",
                        "id": "4wP0"
                    },
                    {
                        "text": "其他，请注明",
                        "id": "5ahJ"
                    }
                ],
                "id": "11sj"
            }
        }
    }
}
```

#### 请求参数 <a href="#e-ae-a-ae-8" id="e-ae-a-ae-8"></a>

路径参数

<table><thead><tr><th width="153.33333333333331">参数名称</th><th width="297.3614457831326">示例</th><th>备注</th></tr></thead><tbody><tr><td>sid</td><td>5cd92958fdce2717546f45e5</td><td>问卷ID，24长度字符串</td></tr></tbody></table>

#### 返回数据 <a href="#e-a-ae-ae-r-8" id="e-a-ae-ae-r-8"></a>

<table><thead><tr><th width="351">名称</th><th width="138">类型</th><th width="123">是否必须</th><th>其他信息</th><th data-hidden>默认值</th><th data-hidden>备注</th></tr></thead><tbody><tr><td>data</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ _id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ status</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ conclusion</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ introduction</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ pages</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>          ├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ questions</td><td>string []</td><td>非必须</td><td>item 类型: string</td><td></td><td></td></tr><tr><td>               ├─</td><td></td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ questions</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ LKQ1</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ blank</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ description</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ lastOptionFixed</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ options</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>                    ├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>                    ├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ preLineNum</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ random</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ randomGroup</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ randomGroupSetting</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>                    ├─ random</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ randomReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ relateBy</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ relateCondition</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ relateFor</td><td>string []</td><td>非必须</td><td>item 类型: string</td><td></td><td></td></tr><tr><td>                    ├─</td><td></td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ required</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ verticalLineNum</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ time</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ displayRules</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ standardizedModelTagConfigs</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ playerType</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ cycleConf</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ activities</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>                    ├─ question_id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ version</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ isSubSurveyMode</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ subSurveys</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ updated_at</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>meta</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ configs</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ accountLimit</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ amsLottery</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ browserLimit</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ callbackUrl</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ canCheckAnswers</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ canPhaseSubmit</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ collectDeadlineMsg</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ collectNotify</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ collectProgress</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ domain</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ forbidUserSelect</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ ipLimit</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ isCanFallback</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ isSaveAnswersHistory</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ language</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ outVerificationRegions</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ outVerificationSkipWelcome</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ outVerificationUseDefault</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ phaseSubmitPages</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ redirect</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ redirectUri</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ showProgress</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ showSerial</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ showWatermark</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ theme</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ useNewLogic</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ verification</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ whitelistLimit</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ whitelistType</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ acceptCheckbox</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ agreement</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr></tbody></table>



### 2. 提交答卷接口

**接口地址**

```
正式地址： https://in.weisurvey.com/v2/api/
测试地址： 
Path： /surveys/:sid
Method： POST
```

**接口描述**

```
{
"fingerprint":"717185371687d903d6c7e25710963045",
"answers":[{"id":"VOJ1","type":"radio","options":[{"id":"YJM2","text":"选项1"}]}],
"time":1577093714,
"continent": "Asia",
"region": "China",
"age": "14 or lower"
}

answers示例：
{
  "i7zq": {
    "id": "i7zq",
    "type": "radio",
    "options": [
      {
        "id": "jpZ5",
        "text": "选项1",
        "checked": true
      },
      {
        "id": "kn74",
        "text": "选项2",
        "checked": false
      }
    ]
  },
  "edw6": {
    "id": "edw6",
    "type": "radio",
    "options": [
      {
        "id": "cHbM",
        "text": "<p><strong>选项1</strong></p>",
        "checked": true
      },
      {
        "id": "dxKd",
        "text": "选项2",
        "checked": false
      }
    ]
  }
}
```

**请求参数**

Headers

<table><thead><tr><th width="156">参数名称</th><th width="207">参数值</th><th>是否必须</th><th>示例</th><th>备注</th></tr></thead><tbody><tr><td>Content-Type</td><td>application/json</td><td>是</td><td></td><td></td></tr></tbody></table>

路径参数

<table><thead><tr><th width="161.33333333333331">参数名称</th><th>示例</th><th>备注</th></tr></thead><tbody><tr><td>sid</td><td>5cd92958fdce2717546f45e5</td><td>问卷ID，24长度字符串</td></tr></tbody></table>

Body

<table><thead><tr><th width="213">名称</th><th width="111">类型</th><th width="101">是否必须</th><th>备注</th><th>其他信息</th><th data-hidden>默认值</th></tr></thead><tbody><tr><td>fingerprint</td><td>string</td><td>必须</td><td>用户指纹</td><td></td><td></td></tr><tr><td>answers</td><td>object</td><td>必须</td><td>答案是动态根据问卷配置来的</td><td></td><td></td></tr><tr><td>     ├─ 1vSZ</td><td>object</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ type</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ options</td><td>object []</td><td>必须</td><td></td><td>item 类型: object</td><td></td></tr><tr><td>               ├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ checked</td><td>boolean</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ 9jXS</td><td>object</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ type</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ options</td><td>object []</td><td>必须</td><td></td><td>item 类型: object</td><td></td></tr><tr><td>               ├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ checked</td><td>boolean</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ 43Yw</td><td>object</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ type</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ options</td><td>object []</td><td>必须</td><td></td><td>item 类型: object</td><td></td></tr><tr><td>               ├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>               ├─ checked</td><td>boolean</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>time</td><td>number</td><td>必须</td><td>时间戳</td><td></td><td></td></tr><tr><td>continent</td><td>string</td><td>非必须</td><td>大洲</td><td></td><td></td></tr><tr><td>region</td><td>string</td><td>非必须</td><td>国家或地区</td><td></td><td></td></tr><tr><td>age</td><td>string</td><td>非必须</td><td>年龄</td><td></td><td></td></tr><tr><td>callback_params</td><td>string</td><td>非必须</td><td>第三方回调自定义参数</td><td></td><td></td></tr><tr><td>channel</td><td>string</td><td>非必须</td><td>渠道</td><td></td><td></td></tr></tbody></table>

**返回数据**

<table><thead><tr><th width="125">名称</th><th>类型</th><th>是否必须</th><th>备注</th><th>其他信息</th><th data-hidden>默认值</th></tr></thead><tbody><tr><td>data</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ id</td><td>string</td><td>非必须</td><td>用户答题ID</td><td></td><td></td></tr></tbody></table>



### **3**. 分段提交答卷接口

**接口地址**

```
正式地址： https://in.weisurvey.com/v2/api/
测试地址： 
Path： /phase-answer/{surveyId}
Method： POST
```

**请求参数**

Headers

<table><thead><tr><th width="159">参数名称</th><th width="188">参数值</th><th>是否必须</th><th>示例</th><th>备注</th></tr></thead><tbody><tr><td>Content-Type</td><td>application/json</td><td>是</td><td></td><td></td></tr></tbody></table>

路径参数

| 参数名称     | 示例 | 备注   |
| -------- | -- | ---- |
| surveyId |    | 问卷id |

Body

<table><thead><tr><th width="176">名称</th><th width="115">类型</th><th width="119">是否必须</th><th>备注</th><th>其他信息</th><th data-hidden>默认值</th></tr></thead><tbody><tr><td>client_id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>query_string</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>time</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>answer_id</td><td>string</td><td>必须</td><td>答卷id</td><td></td><td></td></tr><tr><td>answer_finished</td><td>boolean</td><td>必须</td><td>问卷是否已完成</td><td></td><td></td></tr><tr><td>answers</td><td>object []</td><td>非必须</td><td></td><td>item 类型: object</td><td></td></tr><tr><td>     ├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ type</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ options</td><td>object []</td><td>必须</td><td></td><td>item 类型: object</td><td></td></tr><tr><td>            ├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr></tbody></table>

### **4**. 问卷分发详情接口

**接口地址**

```
正式地址： https://in.weisurvey.com/v2/api/
测试地址：
Path： /survey_distributes/{id}
Method： GET
```

**请求参数**

路径参数

| 参数名称 | 示例 | 备注 |
| ---- | -- | -- |
| id   |    |    |

**返回数据**

<table><thead><tr><th width="192">名称</th><th width="116">类型</th><th width="115">是否必须</th><th width="119">备注</th><th>其他信息</th><th data-hidden>默认值</th></tr></thead><tbody><tr><td>data</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ _id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ tips</td><td>string</td><td>非必须</td><td>提示语</td><td></td><td></td></tr><tr><td>     ├─ random</td><td>boolean</td><td>非必须</td><td>随机排序</td><td></td><td></td></tr><tr><td>     ├─ surveys</td><td>object []</td><td>非必须</td><td>问卷列表</td><td>item 类型: object</td><td></td></tr><tr><td>          ├─ button</td><td>string</td><td>必须</td><td>按钮文本</td><td></td><td></td></tr><tr><td>          ├─ remark</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>          ├─ surveyId</td><td>string</td><td>必须</td><td>问卷id</td><td></td><td></td></tr><tr><td>     ├─ relationships</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr></tbody></table>

### **5**. media资源上传（单文件）

**接口地址**

```
正式地址： https://in.weisurvey.com/v2/api/
测试地址： https://undefined
Path： /media
Method： POST
```

**请求参数**

**Headers**

<table><thead><tr><th width="154">参数名称</th><th width="217">参数值</th><th width="102">是否必须</th><th>示例</th><th>备注</th></tr></thead><tbody><tr><td>Content-Type</td><td>multipart/form-data</td><td>是</td><td></td><td></td></tr></tbody></table>

**Body**

<table><thead><tr><th width="158">参数名称</th><th width="218">参数类型</th><th width="100">是否必须</th><th>示例</th><th>备注</th></tr></thead><tbody><tr><td>attachment</td><td>file</td><td>是</td><td></td><td></td></tr></tbody></table>

**返回数据**

<table><thead><tr><th width="215">名称</th><th width="127">类型</th><th>是否必须</th><th>备注</th><th>其他信息</th><th data-hidden>默认值</th></tr></thead><tbody><tr><td>data</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ file_name</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ file_cdn_url</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ file_origin_url</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ is_success</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr></tbody></table>

### **6**. media资源上传（多文件）

**接口地址**

```
正式地址： https://in.weisurvey.com/v2/api/
测试地址： https://undefined
Path： /media_multi
Method： POST
```

**请求参数**

Headers

<table><thead><tr><th width="160">参数名称</th><th width="197">参数值</th><th width="107">是否必须</th><th>示例</th><th>备注</th></tr></thead><tbody><tr><td>Content-Type</td><td>multipart/form-data</td><td>是</td><td></td><td></td></tr></tbody></table>

Body

<table><thead><tr><th width="166">参数名称</th><th width="193">参数类型</th><th width="106">是否必须</th><th>示例</th><th>备注</th></tr></thead><tbody><tr><td>attachments</td><td>file</td><td>是</td><td></td><td>附件多选</td></tr></tbody></table>

返回数据

<table><thead><tr><th width="210">名称</th><th width="101">类型</th><th width="108">是否必须</th><th width="163">备注</th><th>其他信息</th><th data-hidden>默认值</th></tr></thead><tbody><tr><td>data</td><td>object []</td><td>非必须</td><td></td><td>item 类型: object</td><td></td></tr><tr><td>     ├─ file_name</td><td>string</td><td>必须</td><td>文件名</td><td></td><td></td></tr><tr><td>     ├─ file_cdn_url</td><td>string</td><td>必须</td><td>cdn链接，用于答题端展示</td><td></td><td></td></tr><tr><td>     ├─ file_origin_url</td><td>string</td><td>必须</td><td>真实url，用于提交数据</td><td></td><td></td></tr><tr><td>     ├─ is_success</td><td>boolean</td><td>必须</td><td>该图片是否上传成功</td><td></td><td></td></tr></tbody></table>

### **7**. ams领奖接口

**接口地址**

```
正式地址：https://in.weisurvey.com/v2/api/
测试地址：
Path： /survey/lottery/{id}
Method： POST
```

**接口描述**

```
可能的错误码

'role_parse_failed' => [
    'code'   => 10012,
    'detail' => '角色信息解析失败',
],
'has_not_answered' => [

'code'   => 10013,

'detail' => '还未提交答卷',

],


'survey_configure_error' => [

'code'   => 10014,

'detail' => 'ams配置错误',

],


'ams_lottery_not_configure' => [

'code'   => 10015,

'detail' => '该问卷未配置发奖',

],


'ams_lottery_draw_error' => [

'code'   => 10016,

'detail' => '奖品领取失败',

],


'ams_already_drew' => [

'code'   => 10017,

'detail' => '已经领取过奖品了',

]
```

**请求参数**

**Headers**

<table><thead><tr><th width="163">参数名称</th><th width="151">参数值</th><th width="103">是否必须</th><th width="222">示例</th><th>备注</th></tr></thead><tbody><tr><td>Content-Type</td><td>application/x-www-form-urlencoded</td><td>是</td><td></td><td></td></tr><tr><td>Referer</td><td></td><td>是</td><td>https://test.a.imur.tencent.com/answer?sid=5f16524076051f1332527962&#x26;ADTAG=sid.5f16524076051f1332527962&#x26;lang=zh-CHT&#x26;sPlatId=0&#x26;sArea=1&#x26;sPartition=10019&#x26;sRoleId=7qb-hpfqo-2</td><td>游戏角色参数</td></tr></tbody></table>

**路径参数**

<table><thead><tr><th width="164.33333333333331">参数名称</th><th width="288">示例</th><th>备注</th></tr></thead><tbody><tr><td>id</td><td>5f16527a8787be002e44aef2</td><td>问卷id</td></tr></tbody></table>

**返回数据**

<table><thead><tr><th width="220">名称</th><th>类型</th><th>是否必须</th><th>备注</th><th>其他信息</th><th data-hidden>默认值</th></tr></thead><tbody><tr><td>data</td><td>object</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ package_id</td><td>number</td><td>必须</td><td>礼包id</td><td></td><td></td></tr><tr><td>    ├─ package_name</td><td>string</td><td>必须</td><td>礼包名称</td><td></td><td></td></tr><tr><td>    ├─ package_num</td><td>number</td><td>必须</td><td>礼包数量</td><td></td><td></td></tr></tbody></table>

### 8. ams领奖状态查询接口

**接口地址**

```
正式地址：https://in.weisurvey.com/v2/api/
测试地址：
Path： /survey/lottery/{id}
Method： GET
```

**请求参数**

**路径参数**

<table><thead><tr><th width="151.33333333333331">参数名称</th><th width="222">示例</th><th>备注</th></tr></thead><tbody><tr><td>id</td><td></td><td></td></tr></tbody></table>

**返回数据**

<table><thead><tr><th width="263">名称</th><th width="126">类型</th><th>是否必须</th><th width="153">备注</th><th>其他信息</th><th data-hidden>默认值</th></tr></thead><tbody><tr><td>data</td><td>object</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ _id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ package_group_id</td><td>string</td><td>必须</td><td>礼包组id</td><td></td><td></td></tr><tr><td>     ├─ package_id</td><td>null</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ package_name</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ package_num</td><td>null</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>     ├─ ret_code</td><td>number</td><td>必须</td><td>ams状态码</td><td></td><td></td></tr><tr><td>     ├─ status</td><td>boolean</td><td>必须</td><td>true：领取成功 false：领取失败</td><td></td><td></td></tr></tbody></table>

### 9. 获取用户答案接口

**接口地址**

```
正式地址： https://in.weisurvey.com/v2/api/
测试地址： https://survey.imur.oa.com
Path： /answers/{sid}
Method： GET
```

**请求参数**

**路径参数**

<table><thead><tr><th width="162.33333333333331">参数名称</th><th width="163">示例</th><th>备注</th></tr></thead><tbody><tr><td>sid</td><td></td><td></td></tr></tbody></table>

#### 返回数据 <a href="#e-a-ae-ae-r-7" id="e-a-ae-ae-r-7"></a>

<table><thead><tr><th>名称</th><th>类型</th><th>是否必须</th><th>其他信息</th><th data-hidden>默认值</th><th data-hidden>备注</th></tr></thead><tbody><tr><td>data</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ _id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ answers</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ options</td><td>object []</td><td>必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ name</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ value</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ groups</td><td>object</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ GDTe</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ TCPd</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ XIIj</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ ZALi</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ MHVo</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ YGWn</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ IIPs</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ WTLr</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ subTitles</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ survey</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ pages</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ questions</td><td>string []</td><td>必须</td><td>item 类型: string</td><td></td><td></td></tr><tr><td>├─</td><td></td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questions</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ ATVb</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ abnormalOptionText</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ description</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ fractionReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ hasAbnormalOption</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ maxValue</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ minValue</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateBy</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateCondition</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateFor</td><td>string []</td><td>非必须</td><td>item 类型: string</td><td></td><td></td></tr><tr><td>├─</td><td></td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ required</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ tipsText</td><td>string []</td><td>非必须</td><td>item 类型: string</td><td></td><td></td></tr><tr><td>├─</td><td></td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ DBI1</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ blank</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ description</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ lastOptionFixed</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ options</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ preLineNum</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ random</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomGroup</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomGroupSetting</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ random</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateBy</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateCondition</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateFor</td><td>string []</td><td>非必须</td><td>item 类型: string</td><td></td><td></td></tr><tr><td>├─</td><td></td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ required</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ verticalLineNum</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ JVJ4</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ blank</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ description</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ exclusive</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ lastOptionFixed</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ optionalMax</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ optionalMin</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ options</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ preLineNum</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ random</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomGroup</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomGroupSetting</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ random</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateBy</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateCondition</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateFor</td><td>string []</td><td>非必须</td><td>item 类型: string</td><td></td><td></td></tr><tr><td>├─</td><td></td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ required</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ verticalLineNum</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ MDNz</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ NBDc</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ blank</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ description</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ horizontalDisplay</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ horizontalLineNum</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ lastOptionFixed</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ options</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionLastOptionFixed</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionRandom</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionRandomReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionRelateBy</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionRelateCondition</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ random</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateBy</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateCondition</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ required</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ subTitles</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ verticalDisplay</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ verticalLineNum</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ NDXa</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ description</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ inputMax</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ inputMin</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ inputRule</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ inputSize</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ required</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ PHZp</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ description</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ required</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ uploadMax</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ QHRu</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ description</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ options</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ children</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ name</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ name</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ required</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ subTitles</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ QYOm</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ abnormalOptionText</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ description</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ fractionReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ hasAbnormalOption</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ horizontalDisplay</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ maxValue</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ minValue</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionLastOptionFixed</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionRandom</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionRandomReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionRelateBy</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionRelateCondition</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ required</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ subTitles</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ tipsText</td><td>string []</td><td>非必须</td><td>item 类型: string</td><td></td><td></td></tr><tr><td>├─</td><td></td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ verticalDisplay</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ TCGq</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ description</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ lastOptionFixed</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ limitNum</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ options</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ random</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomGroup</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomGroupSetting</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ random</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateBy</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateCondition</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ required</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ XYW7</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ description</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ lastOptionFixed</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ options</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ preLineNum</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ random</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomGroup</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomGroupSetting</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ random</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateBy</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateCondition</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateFor</td><td>string []</td><td>非必须</td><td>item 类型: string</td><td></td><td></td></tr><tr><td>├─</td><td></td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ required</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ YBAh</td><td>object</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ blank</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ description</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ exclusive</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ horizontalDisplay</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ horizontalLineNum</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ lastOptionFixed</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ optionalMax</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ optionalMin</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ options</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionLastOptionFixed</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionRandom</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionRandomReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionRelateBy</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ questionRelateCondition</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ random</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ randomReverse</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateBy</td><td>null</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ relateCondition</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ required</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ subTitles</td><td>object []</td><td>非必须</td><td>item 类型: object</td><td></td><td></td></tr><tr><td>├─ id</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ text</td><td>string</td><td>必须</td><td></td><td></td><td></td></tr><tr><td>├─ title</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ type</td><td>string</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ verticalDisplay</td><td>boolean</td><td>非必须</td><td></td><td></td><td></td></tr><tr><td>├─ verticalLineNum</td><td>number</td><td>非必须</td><td></td><td></td><td></td></tr></tbody></table>

\
