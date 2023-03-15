# 变量设置（更新中）

支持自定义变量，用于重新组合题目字段，新生成的变量可用于后续的加权、统计和交叉计算

## 【STEP 1】设置变量

<figure><img src="../../.gitbook/assets/image (434).png" alt=""><figcaption><p>设置变量功能入口</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (420).png" alt=""><figcaption><p>变量及有效值定义示例</p></figcaption></figure>

带\*为必填项，同一变量下支持添加多个有效值。有效值的规则按项目需要进行定义。

<figure><img src="../../.gitbook/assets/image (425).png" alt=""><figcaption><p>设置变量</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (406).png" alt=""><figcaption><p>定义多个有效值</p></figcaption></figure>

系统会按照以上有效值的顺序进行匹配，同一条答题数据会被优先匹配在顺序靠前的有效值中；若未满足上述任何条件将置空。

### 变量类型说明

#### 变量类型：单选型、多选型

* 单选型：类似单选题，每个玩家仅能对应一个有效值的变量。【如】性别：男、女
* 多选型：类似多选题，每个玩家可对应一个或多个有效值的变量。【如】常玩品类：动作角色扮演/ARPG类、射击类、即时制MMORPG类、竞速赛车类 、体育运动类

### 如何判断变量类型

有效值的条件中是否包含多选题/矩阵多选题，包含则为多选型变量

### 多选型变量转换为单选型变量

{% hint style="warning" %}
系统当前功能仅支持设置单选型变量，如出现多选型变量，需要把该变量按有效值拆分为多个，每个变量为：**原变量\_有效值：有效值** 或 **原变量\_有效值：是**。
{% endhint %}

<mark style="color:red;">【示例一】</mark>

常玩品类：动作角色扮演/ARPG类、射击类、即时制MMORPG类、竞速赛车类 、体育运动类

**拆分成多个变量为：**

常玩品类\_动作角色扮演/ARPG类：是&#x20;

常玩品类\_射击类：是&#x20;

常玩品类\_即时制MMORPG类：是&#x20;

常玩品类\_竞速赛车类：是&#x20;

常玩品类\_体育运动类：是

<mark style="color:red;">【示例二】</mark>

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>多选型变量按有效值拆分为单选型变量</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>拆分完成效果</p></figcaption></figure>

## 【STEP 2】计算生成变量



## 应用1：参与加权设置

## 应用2：在线查看数据

## 应用3：导出数据

## 应用4：统计图表

## 应用5：交叉分析
