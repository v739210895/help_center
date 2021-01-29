# 开发接口-答题统计

### 逻辑关系AND与OR

AND 在must数组中的每个成员代表一个条件，他们组成的逻辑是：条件1 AND 条件2 AND 条件3

```text
{
    "query": {
        "must": [
            {
                "term": {
                    "FOKc": "123"
                }
            },
            {
                "range": {
                    "OS1d_short": {
                        "gte": 1,
                        "lte": 10
                    }
                }
            },
            {
                "wildcard": {
                    "city": "*"
                }
            },
            ...
        ]
    }
}
```

OR 在should数组中的每个成员代表一个条件，他们组成的逻辑是：条件1 OR 条件2 OR 条件3

```text
{
    "query": {
        "should": [
            {
                "term": {
                    "NDS7": "asd"
                }
            },
            {
                "term": {
                    "NDS7": "fgh"
                }
            },
            ...
        ]
    }
}
```

must和should可以在query中并在，两者是AND的关系。must和should中的每个成员也内嵌套must和should。

### 各种数据类型筛选语法

#### 时间

条件：大于等于、小于等于、范围内

```text
{
    "query": {
        "must": [
            {
                "range": {
                    "created_at": {
                        "gte": "2020-02-20 00:00:00", // 格式为yyyy-MM-dd HH:mm:ss或者毫秒
                        "lte": "2020-02-20 22:00:00"
                    }
                }
            }
        ]
    }
}
```

问卷基础数据中为数值型的字段有： created\_at 答题时间 deleted\_at 删除时间

#### 数值

条件：等于，大于等于、小于等于、范围内

```text
// 等于
{
    "query": {
        "must": [
            {
                "term": {
                    "MNRb_short": 2
                }
            }
        ]
    }
}
```

```text
// 范围：
{
    "query": {
        "must": [
            {
                "range": {
                    "OS1d_short": {
                        "gte": 1, // 大于等于
                        "lte": 10 // 小于等于
                    }
                }
            }
        ]
    }
}
```

在问卷题型中数值型的类型的数据都以`_short`为后缀。 另外，问卷基础数据中为数值型的字段有： answer\_consumed 答题时长

#### 字符串

条件：等于、不等于

```text
{
    "query": {
        "must": [
            {
                "bool": { // 不等于
                    "must_not": [
                        {
                            "terms": { // 使用terms精准多值匹配
                                "BIH7": ["KJX8"]
                             }
                        }
                    ]
                }
            },
            {
                "terms": { // 等于
                    "BIH7": ["KJX7"]
                }
            }
        ]
    }
}
```

条件：模糊匹配

```text
{
    "query": {
        "must": [
            {
                "match": {
                    "BIH7": "xxxx"
                }
            }
        ]
    }
}
```



### 固定字段说明

| 字段 | 说明 |
| :--- | :--- |
| answer\_consumed | 答题时间 |
| city | 城市 |
| os | 操作系统 |
| channel | 渠道，空渠道用 “-” 替代 |

