# 数据清洗

系统提供数据清洗功能，适用场景：投放完成后按指定条件把不符合要求的样本剔除，[在线查看答题数据](../../../cao-zuo-zhi-yin/tong-ji-fen-xi/da-ti-shu-ju-zai-xian-cha-kan.md)/[导出数据](../../../cao-zuo-zhi-yin/xia-zai-shu-ju/)中，不合格样本被标记为无效。

![数据清洗](<../../../.gitbook/assets/image (77).png>)

## 【STEP 1】设置清洗条件

在“统计”-“数据清洗”页面中，点击右上角“新增条件”即可创建一条新的清洗条件。

### 创建清洗条件

![创建清洗条件](<../../../.gitbook/assets/image (266).png>)

### 设置条件及规则的and、or关系

![设置清洗规则](<../../../.gitbook/assets/image (786).png>)

{% hint style="info" %}
**操作提示**

在选择选项时，如需连续n个，在下拉列表中：点选首个选项->按住shift->点选末个选项，松开shift，即可实现连选
{% endhint %}

![设置条件（组）之间的and、or关系](<../../../.gitbook/assets/image (76).png>)

{% hint style="info" %}
**操作提示**

支持用条件/条件组来设置复杂表达式的清洗规则，可实现条件之间的嵌套



【例】需要清洗掉关于“沙盒游戏时间”前后说法不一致的答题记录：

Q9沙盒类的游戏时间 选中 小于5小时&#x20;

**and**&#x20;

（Q10.1 A类的沙盒游戏时间 选中 5小时以上的选项 **or** Q10.2 B类的沙盒游戏时间 选中 5小时以上的选项 **or** Q10.3 C类的沙盒游戏时间 选中 5小时以上的选项 **or** Q10.4 D类的沙盒游戏时间 选中 5小时以上的选项）


{% endhint %}

![【例】复杂清洗条件 --嵌套条件组](<../../../.gitbook/assets/image (81).png>)

## 【STEP 2】保存并执行清洗

设置完所有清洗条件后，点击右上角“保存条件”“执行清洗”，即可触发清洗任务。

![保存条件](<../../../.gitbook/assets/image (623).png>)

{% hint style="warning" %}
执行清洗必须在投放结束后，触发执行清洗前务必先“暂停回收”
{% endhint %}

## 【STEP 3】查看数据

执行完成后，页面会显示每个条件被清洗掉的无效答卷数量。

![清洗完成](<../../../.gitbook/assets/image (217).png>)

前往[在线查看答题数据](../../../cao-zuo-zhi-yin/tong-ji-fen-xi/da-ti-shu-ju-zai-xian-cha-kan.md) 或 [导出数据](../../../cao-zuo-zhi-yin/xia-zai-shu-ju/)，可查看被标记为无效的答题记录。

![](<../../../.gitbook/assets/image (653).png>)
