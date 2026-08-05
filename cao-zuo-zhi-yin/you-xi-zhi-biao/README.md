# 🆕 游戏指标打通

问卷系统支持调研数据与游戏指标数据打通，结合答题者的主观态度与客观行为进行分析。

在游戏完成接入后，用户可在问卷系统平台上选取本次调研所需打通的游戏指标并自助**提取数据**，系统**在线计算**结果数据，同时支持用户**下载**打通后数据表。

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

![调研数据与游戏指标打通 - 数据表](<../../.gitbook/assets/image (684).png>)

## 【前置工作】游戏接入及权限申请

{% hint style="info" %}
【指引】游戏指标数据接入及功能使用 [https://iwiki.woa.com/p/1674316383](https://iwiki.woa.com/p/1674316383)
{% endhint %}

![接入流程](<../../.gitbook/assets/image (692).png>)

## &#x20;1. 选取游戏指标

问卷开始投放后，前往“游戏指标”模块可提取**已答题玩家**的游戏指标数据。

### 1.1 设置游戏指标

先选定本次调研所需使用的游戏指标，保存后系统将自动执行提取，支持二次编辑（新增/删除指标）。

每份问卷仅能生成一份提取任务，该问卷的所有负责人和关注人共同管理，新增/删除指标前请内部沟通确认。

{% hint style="info" %}
数据提取规则说明：

1. 问卷系统按玩家提交答卷的时间，提取该**玩家答题当天**的游戏指标数据
2. 由于经分侧生成游戏指标数据为次日，请在玩家填答后的次日前往本系统提取数据

【例】

玩家A在游戏&#x5185;**{5月6日}**&#x7B54;题，经分侧&#x5728;**{5月7日}**&#x624D;生成玩家A在5月6日的游戏指标记录，需要&#x5728;**{5月7日}**&#x624D;能到问卷系统提取该玩家的调研数据+游戏指标，在此前仅能获取该玩家的调研数据。
{% endhint %}

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

### 1.2 更新指标数据

支持实时更新数据，更新方式为全量刷新；更新过程中统计图表功能可正常使用

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

## 2. 导出数据表

### 2.1 导出原始数据

1. 点击显示下拉框，选择导出原始数据，即可导出该问卷的全部原始答题数据+游戏指标数据+自定义指标数据
2. 导出的文件名称为：项目名称\_answers.csv
3. 文件采用异步下载方式，任务导出状态显示在离线下载弹窗中，导出后完成下载

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

### 2.2 导出编码数据

1. 点击显示下拉框，选择导出原始数据，即可导出该问卷的全部原始答题数据+游戏指标数据+自定义指标数据
2. 导出的答题编码数据为.tar格式的压缩包，内含答题编码数据（.csv）和SPSS编码（.txt）
3. 文件采用异步下载方式，任务导出状态显示在离线下载弹窗中，导出后完成下载

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

![答题编码数据压缩包](../../.gitbook/assets/image33.png)

## 3. 统计图表

支持在线查看统计结果

### 3.1 统计图表

统计图表页支持在线查看答题数据和指标数据的统计结果

1. 左侧大纲展示问卷题目和游戏指标，自由勾选显示的问卷题目和游戏指标，取消勾选后右侧不显示对应题目或指标
2. 游戏指标支持分三个层级展示：模块——指标维度——指标名称
3. 支持对问卷题目和指标进行关键词搜索过滤

{% hint style="info" %}
统计说明：百分比=该项小计/该指标的总计\*100%，保留两位小数
{% endhint %}

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

### 3.2 数据筛选

统计图表提供数据筛选功能，开启后可设定指定条件对当前已回收的答卷数据和指标数据进行筛选

{% hint style="info" %}
关闭或刷新页面，将清空筛选条件并展示全部答题数据和指标数据

筛选条件仅当次有效，不保存记录

支持一键清空条件，操作不可撤回
{% endhint %}

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

### 3.3 导出统计结果

支持在线导出统计结果

{% hint style="info" %}
1. 未设置筛选条件时，点击导出统计结果即可下载全部数据，包含问卷数据+指标数据
2. 设置筛选条件后，须点击开始筛选，筛选成功即可导出基于筛选条件下展示的所有数据
3. 统计说明：百分比=该项小计/该指标的总计\*100%，保留两位小数
{% endhint %}

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

###



## 4. 自定义组合指标

支持自定义指标，用于组合游戏指标和题目字段，新生成指标可用于后续的统计和交叉计算

带\*为必填项，同一指标支持添加多个有效值

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

