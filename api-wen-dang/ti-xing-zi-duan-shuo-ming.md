# 题型字段说明

## 题型公共字段 Question

> 每个题型均会包含以下字段

| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| id | string | 一份问卷内的唯一id |
| type | string | 题目类型 |
| title | string | 题目标题 |
| description | string | 题目描述 |
| required | boolean | 是否必答 |

## 选项字段 Option

> 选项中包含的字段

| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| id | string | 选项id |
| text | string | 选项文本 |
| blank | boolean | 该选项是否开启填空 |
| blankRequired | boolean | 填空必填 |
| noRandom | boolean | 该选项是否不随机 |
| exclusive | boolean | 该选项是否跟其他选项互斥 |

## 随机排序相关字段 Random

| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| random | boolean | 选项是否随机 |
| questionRandom | boolean | 子问题是否随机 |
| randomReverse | boolean | 选项是否随机正逆序 |
| questionRandomReverse | boolean | 子问题是否随机正逆序 |
| lastOptionFixed | boolean | 是否固定最后一个选项 |
| questionLastOptionFixed | boolean | 子问题是否固定最后一项 |
| randomGroup | boolean | 是否开启选项随机分组 |
| randomGroupSetting | object | 随机分组设置 |
| randomGroupSetting.random | boolean | 分组间随机排序 |
| randomGroupSetting.options | \[\]object | 分组选项 |
| randomGroupSetting.options.\*.groupIndex | number | 分组序号 |
| randomGroupSetting.options.\*.isGroup | boolean | 是否是一个组 |
| randomGroupSetting.options.\*.num | number | 该组随机展示n项 |
| randomGroupSetting.options.\*.optionIds | string\[\] | 选项id数组 |

## 子问题 SubTitle

| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| id | string | 子问题id |
| text | string | 子问题文本 |

## 附件题 Attachment

| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| uploadMax | number | 最大上传数量 |

## 级联题 Cascade

| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| subTitles | array | 二级标题列表 |
| options | \[\]object | 题目选项 |
| options.\*.id | string | 选项id |
| options.\*.name | string | 选项名称 |
| options.\*.children | \[\]object | 子选项 |

## 多选题 \| 单选题 \| 下拉题  Checkbox \| Radio \| Select

| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| relateBy | string | 关联自某一个问题 |
| relateCondition | string | 关联的条件：选中、未选中、显示等 |
| relateFor | \[\]string | 被某一个或者多个问题关联 |
| options | \[\]object | 题目选项 |
| blank | boolean | 是否开启填空 |
| preLineNum | number | 每行展示多少个选项 |
| optionalMin | number | 最少选择多少项 |
| optionalMax | number | 最多选择多少项 |
| exclusive | boolean | 是否开启互斥 |

## 矩阵多选 \| 矩阵单选 MatrixCheckbox \| MatrixRadio

| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| relateBy | string | 选项关联自某一个问题 |
| questionRelateBy | string | 子问题关联自某一个问题 |
| relateCondition | string | 选项关联的条件：选中、未选中、显示等 |
| questionRelateCondition | string | 子问题关联的条件：选中、未选中、显示等 |
| subTitles | string\[\] | 子问题列表 |
| optionalMin | number | 最少选择多少项 |
| optionalMax | number | 最多选择多少项 |
| exclusive | boolean | 是否开启互斥 |

## 矩阵量表 \| 量表题 MatrixRange \| Range

| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| minValue | number | 最低分 |
| maxValue | number | 最高分 |
| tipsText | string\[\] | 提示文本 |
| fractionReverse | boolean | 分数是否反转 |
| hasAbnormalOption | boolean | 是否有异常项 |
| abnormalOptionText | boolean | 异常项文本 |

## 主观题 Subjective

| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| inputSize | string | 输入框大小 |
| inputRule | string | 输入文本校验规则: number, letter, chinese, email, phone, any |
| inputMin | number | 至少输入多少字 |
| inputMax | number | 至多输入多少字 |

