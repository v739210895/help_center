---
description: >-
  可以控制指定选项的被选次数，当达到指定次数后，选择了此选项的问卷会被标记为配额无效答卷。例如，一份问卷需要收集的答卷是男，女各500份，就可以通过设置配额来控制
---

# 配额设置

配额设置仅支持单选题、多选题、联动题(需导入地址）

### 【STEP 1】添加渠道

进入配额设置后可以先增加投放渠道，对每个渠道回收数据进行配额（如不分渠道投放点击下一步即可）

<figure><img src="../../.gitbook/assets/image (825).png" alt=""><figcaption><p>添加渠道</p></figcaption></figure>

### 【STEP 2】设置配额题目

将左侧题目列表中的题目拖拽到右侧配额题目即可生成配额

<figure><img src="../../.gitbook/assets/image (828).png" alt=""><figcaption><p>添加配额题目</p></figcaption></figure>

### 【STEP 3】设置配额数量

设置每个选项的配额数量，默认0为不限制配额

<figure><img src="../../.gitbook/assets/image (829).png" alt=""><figcaption><p>设置配额数量</p></figcaption></figure>

### 【STEP 4】查看配额进度

回收问卷后可直接在当前页查看配额完成情况

<figure><img src="../../.gitbook/assets/image (830).png" alt=""><figcaption></figcaption></figure>

### 设置交叉配额

通过设置交叉配额，可以根据2个题目来限定选项可选择的次数。例如：需收集10个喜欢电脑游戏的男性玩家答卷，可以使用交叉配额来完成，设置如下图所示，拖拽列表中的题目到需参与交叉配额的题目下方

<figure><img src="../../.gitbook/assets/交叉配额1.gif" alt=""><figcaption><p>交叉配额</p></figcaption></figure>

### 有效问卷回收量上限

{% hint style="info" %}
有效问卷达到预设值后，将自动暂停回收；

可对每个投放渠道分别设置有效问卷回收量，有效问卷量上限后该渠道链接自动暂停回收，其他渠道正常回收问卷。
{% endhint %}

<figure><img src="../../.gitbook/assets/image (23) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### 添加变量

支持自定义变量，即重新组合题目字段生成新变量，新生成的变量可参与配额或与其他题目生成交叉配额

<figure><img src="../../.gitbook/assets/image (832).png" alt=""><figcaption><p>添加变量</p></figcaption></figure>

添加成功后，会在题目列表下方生成新的变量题目，拖拽即可参与配额

<figure><img src="../../.gitbook/assets/image (833).png" alt=""><figcaption></figcaption></figure>
