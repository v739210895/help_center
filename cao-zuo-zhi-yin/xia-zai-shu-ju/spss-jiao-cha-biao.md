# SPSS交叉表

系统提供导出用于生成交叉表的SPSS代码，在SPSS中导入数据和编码后，可直接运行此代码在SPSS中生成交叉表。

![导出编码数据-交叉表](<../../.gitbook/assets/image (508).png>)

{% hint style="info" %}
1. 代码用于生成问卷中**所有题目**的交叉表
2. 支持题型：单选题、下拉题、量表题、多选题、矩阵单选题、矩阵量表题、矩阵多选题，其他题型不参与生成交叉表

注：系统默认对所有支持的题目进行交叉，直接运行全部代码可能导致SPSS运行卡顿，请按需删减行、列表头
{% endhint %}

## 【STEP 1】导入编码数据及SPSS编码

操作步骤可参考“[SPSS数据分析](spss-shu-ju-fen-xi.md)”一节

## 【STEP 2】导入交叉表代码

把CTABLES.txt中的代码全选复制粘贴到SPSS的语法编辑器中，或解压后在PSS中通过“文件”-“打开”-“语法”打开CTABLES.txt文件。

![CTABLES.txt中的代码](<../../.gitbook/assets/image (366).png>)

## 【STEP 3】编辑与运行

按需删减行、列表头，选中代码后，点击运行，即开始计算生成交叉表。（可能会由于语法句子过长而出现红字报错信息，不影响生成交叉表）

![运行交叉表代码](<../../.gitbook/assets/image (349).png>)

{% hint style="warning" %}
在/TABLE行中，BY前的为行表头，BY后的为列表头
{% endhint %}

![行、列表头示例](<../../.gitbook/assets/image (50).png>)

## 【STEP 4】生成交叉表

生成的交叉表在输出窗口显示。

![生成交叉表](<../../.gitbook/assets/image (583).png>)

