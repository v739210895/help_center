# SPSS数据分析

## 【STEP 1】导出答题数据及SPSS编码

在“我的问卷”列表中导出“答题编码数据”，在“离线下载”中下载对应的.zip文件，文件中包括：答题数据（.csv）、SPSS编码文件（.txt）、交叉表代码(.txt)。

![导出数据并下载](<../../.gitbook/assets/Snipaste_2023-10-09_10-13-00 (1).png>)

![导出的文件](<../../.gitbook/assets/Snipaste_2023-10-09_10-27-02 (1).png>)

## 【STEP 2】导入答题数据

解压压缩包文件后，在SPPS中打开答题数据（.csv）文件，开始导入。

![SPSS中文本导入的第一步](<../../.gitbook/assets/image (548).png>)

变量排列中选择“分隔”，变量名称是否包括在文件顶部中选择“是”，点击“下一步”。

![SPSS中文本导入的第二步](<../../.gitbook/assets/image (96).png>)

选择“每一行表示一个个案”，导入“全部个案”，点击“下一步”。

![SPSS中文本导入的第三步](<../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png>)

变量分隔符中选择“逗号”，文本限定符选择“双引号”，点击“下一步”。

![SPSS中文本导入的第四步](<../../.gitbook/assets/image (438).png>)

检查确认变量名称及数据格式，点击“下一步”。

![SPSS中文本导入的第五步](<../../.gitbook/assets/image (220).png>)

完成导入。

![SPSS中文本导入的第六步](<../../.gitbook/assets/image (214).png>)

![答题数据导入完成](<../../.gitbook/assets/image (144).png>)

## 【STEP 3】导入答题编码

导入答题数据后，变量视图中的标签和值均为空，需要导入答题编码。

![变量视图中的标签和值](<../../.gitbook/assets/image (22) (1) (1) (1) (1) (1).png>)

在STEP2已导入答题数据的基础上，点击“文件”-“打开”-“语法”，选择压缩包中解压出来的SPSS编码文件（.txt），打开。

![打开SPSS编码文件（.txt）](<../../.gitbook/assets/image (578).png>)

全选后，运行编码。

![运行编码](<../../.gitbook/assets/image (178).png>)

运行成功后，“变量视图”中的标签的值都导入了内容。

![导入编码完成](<../../.gitbook/assets/image (451).png>)

## 常见问题

### 为什么导入答题编码后，出现报错？

![导入答题编码后，查看器出现报错信息](<../../.gitbook/assets/image (597).png>)

这是由于在“[**【STEP 2】导入答题数据**](spss-shu-ju-fen-xi.md#step-2-dao-ru-da-ti-shu-ju)”步骤中，对多选题/矩阵多选题的同一题n列未设置统一数据类型导致的。可按照下图提示，在SPSS数据编辑器的“变量视图”中，调整对应列的数据类型后，重新按“[**【STEP 3】导入答题编码**](spss-shu-ju-fen-xi.md#step-3-dao-ru-da-ti-bian-ma)”步骤操作。

![调整数据类型  ](<../../.gitbook/assets/image (19) (1) (1) (1) (1) (1).png>)
