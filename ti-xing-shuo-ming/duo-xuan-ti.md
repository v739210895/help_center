# 多选题

多选题指从一组选项当中，选出其中一个或多个作为正确的答案，可指定选择数量的范围。

![多选题](<../.gitbook/assets/image (486).png>)

## 【STEP 1】 新建多选题

在问卷编辑页中，选择左侧题型控件中的“多选题”或在指定题目点击右侧快捷工具栏中的+按钮选择“多选题”即可新建多选题。

![通过“题型”控件新建多选题](../.gitbook/assets/Snipaste_2023-10-10_10-12-13.png)

![在指定题目下方新建多选题](../.gitbook/assets/Snipaste_2023-10-10_10-12-51.png)

## 【STEP 2】编辑题目、备注、选项内容

题目、选项及备注均支持富文本编辑，包括：字体样式、[插入超链接](../cao-zuo-zhi-yin/wen-juan-bian-ji/cha-ru-chao-lian-jie.md)、[插入图片](../cao-zuo-zhi-yin/wen-juan-bian-ji/cha-ru-tu-pian.md)、[插入视频](../cao-zuo-zhi-yin/wen-juan-bian-ji/cha-ru-shi-pin.md)、[引用选项内容](../cao-zuo-zhi-yin/wen-juan-bian-ji/nei-rong-yin-yong.md)。

![多选题内容编辑](../.gitbook/assets/Snipaste_2023-10-10_10-13-16.png)

## 【STEP 3】题目及选项设置

### 必答设置

在右侧面板中关闭“此题必答”功能后，答题时此题可以为空。

{% hint style="info" %}
所有题目默认开启“此题必答”功能。
{% endhint %}

![“此题必答”功能](../.gitbook/assets/Snipaste_2023-10-10_10-15-46.png)

### 题型切换

单选题、多选题、下拉题之间可自由切换，切换后原题目的必答设置、选项关联设置、选项随机设置均保留。

![](../.gitbook/assets/Snipaste_2023-10-10_10-16-22.png)

### 在选项后添加填空框

开启后，在选项后方增加填空框，勾选必填，用户须填写内容后才可提交，适用于用户选择其他项后，收集其他相关信息的场景

<figure><img src="../.gitbook/assets/Snipaste_2023-10-10_10-25-27.png" alt=""><figcaption></figcaption></figure>

### 可选范围

多选题中，可限制同一问题中用户可选择的选项数量。

![设置可选范围](../.gitbook/assets/Snipaste_2023-10-10_10-17-03.png)

### 选项关联

选项关联即让答题者选中（或未选中）的选项显示在下一题的可选项中，一般用于题目相关性极高的两题中或追问的情况。

![选项关联](../.gitbook/assets/Snipaste_2023-10-10_10-18-45.png)

{% content-ref url="../cao-zuo-zhi-yin/wen-juan-bian-ji/xuan-xiang-she-zhi/xuan-xiang-guan-lian.md" %}
[xuan-xiang-guan-lian.md](../cao-zuo-zhi-yin/wen-juan-bian-ji/xuan-xiang-she-zhi/xuan-xiang-guan-lian.md)
{% endcontent-ref %}

### 选项分列

在题目编辑状态下，可设置选项分列，设置成功后，在答题端会根据设置的每行展示选项个数对选项进行分列展示，横屏下可设置每行展示1\~6个，竖屏下可设置每行展示1\~3个。适用于选项数量多且选项文本不长的情况。

![选项分列设置](../.gitbook/assets/Snipaste_2023-10-10_10-21-26.png)

![电脑答题端显示](<../.gitbook/assets/image (276).png>)

### 选项互斥

多选题中的选项互斥指的是指定某个选项为互斥项，答题时若用户选择了任一被设置为互斥项的选项，则不可选择其他选项。

![选项互斥](../.gitbook/assets/Snipaste_2023-10-10_10-32-11.png)

### 选项随机

在题目编辑状态下，可设置选项随机，设置成功后，在答题端会根据所选择的随机方式显示选项。随机方式包括：随机排序、随机正逆序、分组显示。

#### 选项随机排序

选项随机排序是指答题时题目中的选项以随机顺序出现。开启“选项随机排序”功能后，题目的选项右侧会出现不随机的勾选框，若希望某个选项固定在当前位置，可在其后勾选“不随机”，则该选项不参与随机排序。

![选项随机排序](../.gitbook/assets/Snipaste_2023-10-10_11-24-49.png)

#### 选项随机正逆序

选项随机正逆序是指答题时题目中的选项随机以正序/逆序出现。开启“选项随机正逆序”功能后，“选项随机正逆序”功能下方会出现“固定最后一个选项”功能开关，若希望最后一个选项固定在当前位置，可开启“固定最后一个选项”功能，则在答题端显示时最后一个选项不参与随机正逆序。

![选项随机正逆序](../.gitbook/assets/Snipaste_2023-10-10_14-36-33.png)

#### 选项分组显示

选项分组显示是指把选项自由划分为多个组别，答题时每个分组的选项随机抽出一个或多个显示，支持分组间随机排序显示，设置方式详见[选项分组显示设置](../cao-zuo-zhi-yin/wen-juan-bian-ji/xuan-xiang-she-zhi/xuan-xiang-sui-ji.md#xuan-xiang-fen-zu-xian-shi)。

![选项分组显示](../.gitbook/assets/Snipaste_2023-10-10_14-37-59.png)

{% content-ref url="../cao-zuo-zhi-yin/wen-juan-bian-ji/xuan-xiang-she-zhi/xuan-xiang-sui-ji.md" %}
[xuan-xiang-sui-ji.md](../cao-zuo-zhi-yin/wen-juan-bian-ji/xuan-xiang-she-zhi/xuan-xiang-sui-ji.md)
{% endcontent-ref %}

## 编辑页及答题端显示

编辑完成后，在编辑页内可查看多选题的具体内容及选项的关联、内容引用、填空设置。

![编辑页内的多选题显示](<../.gitbook/assets/image (362).png>)

![答题端的多选题显示](<../.gitbook/assets/image (625).png>)

## 统计结果展示

在统计分析页中，以小计+条形百分比的形式展示多选题的填答结果。

![多选题统计结果](../.gitbook/assets/Snipaste_2023-10-10_14-38-41.png)

