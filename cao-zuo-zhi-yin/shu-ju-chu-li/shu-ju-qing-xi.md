# 数据清洗

系统提供数据清洗功能，适用场景：投放完成后按指定条件把不符合要求的样本剔除，不合格样本将被标记为无效，不参与统计及交叉计算。

## 【STEP 1】设置清洗条件

在“数据处理”-“数据清洗”页面中，点击右上角“新增条件”即可创建新的清洗条件。

<figure><img src="../../.gitbook/assets/image (423).png" alt=""><figcaption></figcaption></figure>

### 类型一：常规清洗

<figure><img src="../../.gitbook/assets/image (408).png" alt=""><figcaption><p>设置常规清洗规则</p></figcaption></figure>

{% hint style="info" %}
**操作提示**

在选择选项时，如需连续n个，在下拉列表中：点选首个选项->按住shift->点选末个选项，松开shift，即可实现连选
{% endhint %}

#### 设置条件及规则的and、or关系

{% hint style="info" %}
**操作提示**

支持用条件/条件组来设置复杂表达式的清洗规则，可实现条件之间的嵌套

<mark style="color:red;">【例】</mark>需要清洗关于“沙盒游戏时间”前后说法不一致的答题记录：

Q9沙盒类的游戏时间 选中 小于5小时&#x20;

**and**&#x20;

（Q10.1 A类的沙盒游戏时间 选中 5小时以上的选项&#x20;

**or** Q10.2 B类的沙盒游戏时间 选中 5小时以上的选项&#x20;

**or** Q10.3 C类的沙盒游戏时间 选中 5小时以上的选项&#x20;

**or** Q10.4 D类的沙盒游戏时间 选中 5小时以上的选项）
{% endhint %}

### 类型二：智能清洗

系统支持对矩阵单选、矩阵多选、矩阵量表进行智能清洗，若玩家在矩阵题中全部子问题都选择同一选项，则判断此答卷为乱填答，系统将把此答卷标记为“无效”。

<figure><img src="../../.gitbook/assets/image (424).png" alt=""><figcaption><p>设置智能清洗</p></figcaption></figure>

{% hint style="info" %}
**清洗机制说明**

智能清洗将根据玩家在该矩阵题中提交的答案进行判断，如玩家提交的该矩阵题多个子问题答案完全一致，则被判断为无效。参考下图：

<img src="../../.gitbook/assets/image (398).png" alt="" data-size="original">
{% endhint %}

## 【STEP 2】保存并执行清洗

设置完所有清洗条件后，点击右上角“保存条件”“执行清洗”，即可触发清洗任务。

<figure><img src="../../.gitbook/assets/image (399).png" alt=""><figcaption><p>执行清洗</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (397) (1).png" alt=""><figcaption><p>清洗中</p></figcaption></figure>

## 【STEP 3】查看数据

执行完成后，页面会显示每个条件被清洗掉的无效答卷数量。**被标记为无效的答卷，不参与到导出、统计及交叉分析**。

<figure><img src="../../.gitbook/assets/image (417).png" alt=""><figcaption><p>清洗执行情况</p></figcaption></figure>

前往“答题数据”，可查看被标记为无效的答题记录。

<figure><img src="../../.gitbook/assets/image (407) (1).png" alt=""><figcaption></figcaption></figure>
