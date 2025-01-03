# Weight Distribution



The weight distribution requires respondents to allocate a certain total weight to several options to indicate the importance or priority of each option. It is applicable in scenarios where survey respondents' attitudes towards multiple options are being assessed.



![权重分配题效果](<../../.gitbook/assets/image (636).png>)

## 【STEP 1】 新建权重分配题

在问卷编辑页中，选择左侧题型控件中的“权重分配题”或在指定题目点击右侧快捷工具栏中的+按钮选择“权重分配题”即可创建题目。

![通过“题型”控件新建权重分配题](../../.gitbook/assets/Snipaste_2023-10-16_11-22-19.png)

![在指定题目下方快速创建权重分配题](../../.gitbook/assets/Snipaste_2023-10-16_11-22-56.png)

## 【STEP 2】Edit title, notes, and option content

The title, options, and remarks all support rich text editing, including: font styles.Insert hyperlink, insert image, insert video, quote survey content.

![题目内容编辑](<../../.gitbook/assets/image (663).png>)

## 【STEP 3】题目设置

### 必答设置

在右侧面板中关闭“此题必答”功能后，答题时此题可以为空。

{% hint style="info" %}
所有题目默认开启“此题必答”功能。
{% endhint %}

![必答设置](../../.gitbook/assets/Snipaste_2023-10-16_11-23-58.png)

### 选项关联

选项关联即让答题者选中（或未选中）的选项显示在下一题的可选项中，一般用于题目相关性极高的两题中或追问的情况。

{% hint style="info" %}
仅支持关联单选题、多选题、下拉题的选项
{% endhint %}

![选项关联](../../.gitbook/assets/Snipaste_2023-10-16_11-25-39.png)

### 调整权重总和

权重分配题可支持调整权重总和：总和100或总和10。

{% hint style="warning" %}
在已有回收答题数据的情况下，不可再调整权重总和
{% endhint %}

![调整权重总和](../../.gitbook/assets/Snipaste_2023-10-16_11-26-11.png)

### 选项随机

在题目编辑状态下，可设置选项随机，设置成功后，在答题端会根据所选择的随机方式显示选项。随机方式包括：随机排序、随机正逆序、分组显示。

![选项随机的三种方式](../../.gitbook/assets/Snipaste_2023-10-16_11-26-48.png)

#### 选项随机排序

选项随机排序是指答题时题目中的选项以随机顺序出现。开启“选项随机排序”功能后，题目的选项右侧会出现不随机的勾选框，若希望某个选项固定在当前位置，可在其后勾选“不随机”，则该选项不参与随机排序。

#### 选项随机正逆序

选项随机正逆序是指答题时题目中的选项随机以正序/逆序出现。开启“选项随机正逆序”功能后，“选项随机正逆序”功能下方会出现“固定最后一个选项”功能开关，若希望最后一个选项固定在当前位置，可开启“固定最后一个选项”功能，则在答题端显示时最后一个选项不参与随机正逆序。

#### 选项分组显示

选项分组显示是指把选项自由划分为多个组别，答题时每个分组的选项随机抽出一个或多个显示，支持分组间随机排序显示。

## 答题端显示

编辑完成后，在答题端内可查看当前权重分配题效果。

![答题端显示](<../../.gitbook/assets/image (636).png>)

## 查看答题数据

在统计页的“答题数据”可查看每个答题者对本题选项的打分情况。

![查看答题数据](../../.gitbook/assets/Snipaste_2023-10-16_11-28-14.png)

## 统计结果展示

在统计分析页中，可查看本题中各选项的分值情况。当设置权重总和为100时，系统将自动均分为5个分段、10个分段，可按需切换查看。

![在线统计](../../.gitbook/assets/Snipaste_2023-10-16_11-29-24.png)
