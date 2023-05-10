# 导出的用户id(openid)显示不完整？

## 导出的csv文件，直接使用excel打开后，uid显示成科学计数法怎么办？

直接使用excel打开csv文件可能会导致所收集的手机号码、uid等长数字显示错乱，如显示为科学计数法，查看时尾数显示为0000。

这是由于excel自动将长数字串识别为数字格式，而非文本格式导致的。此时可将（1）csv文件重新导入到excel，（2）或使用SPSS软件打开csv文件；成功打开后，uid可显示为完整的文本内容。             &#x20;

![uid列显示为科学计数法](<../../.gitbook/assets/image (813).png>)

## EXCEL导入csv文件操作步骤

### **【STEP 1】创建EXCEL文档**

创建一个Excel文档（格式可以为 xls 或 xlsx 都可以），用于存放导入的目标数据。

![新建空白文档](<../../.gitbook/assets/image (286).png>)

### **【STEP 2】选择自文本导入**

鼠标选择第一个单元格（第一行A列的单元格），选择EXCEL文档中的“数据”-“自文本”，在弹窗中选择需要查看的csv文件（csv文件需提前解压到文件夹），开始导入。

![csv文件导入](<../../.gitbook/assets/image (59).png>)

### **【STEP 3】导入设置**

不同的excel版本导入时会显示不同的导入设置，大家可按照下方说明查看不同的excel版本的操作。

#### EXCEL 2013

1. 选择使用“分隔符号”，勾选“数据包含标题”，点击“下一步”。

![选择使用“分隔符号”，勾选“数据包含标题”](<../../.gitbook/assets/image (815).png>)

2\. 选择分隔符为“逗号”。

![选择分隔符为“逗号”](<../../.gitbook/assets/image (223).png>)

3\. 在下方“数据预览”中鼠标点选第一列id后，按住键盘的shift不放，鼠标横拽至最后一列，点选最后一列，放开shift键，此时已全选所有列；全选后，在列数据格式中选择“文本”，点击完成。

![全选数据列，并选择数据格式为“文本”](<../../.gitbook/assets/image (345).png>)

#### EXCEL 2016/2019

1. 在导入设置弹窗中，分隔符选择“**逗号**”，点击“**转换数据**”，进入下一步。

<figure><img src="../../.gitbook/assets/image (643).png" alt=""><figcaption></figcaption></figure>

2\. 在弹出的**Power Query编辑器**中选中用户ID列（收集手机号的题目列操作相同），在“”**数据类型**”中选择“**文本**”

<figure><img src="../../.gitbook/assets/image (412).png" alt=""><figcaption></figcaption></figure>

3\. 确认替换

<figure><img src="../../.gitbook/assets/image (416).png" alt=""><figcaption></figcaption></figure>

4\. 替换完成后，数据显示为完整的用户id，点击**关闭并上载**即完成导入

<figure><img src="../../.gitbook/assets/image (432).png" alt=""><figcaption></figcaption></figure>

