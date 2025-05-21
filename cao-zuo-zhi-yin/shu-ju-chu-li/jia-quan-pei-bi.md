# 加权配比

系统提供加权配比功能，适用场景：当某些类型的调查受访者人数不足或过多时，按目标所需占比调整样本结构。

支持两种权重设置方案：

* 常规加权（因子加权）：为总计 100% 的每个回复组指定目标百分比
* 边缘加权：也被称为迭代比例拟合或随机迭代法。它适用的情况是：您需要调整采样群体以满足目标群体的代表，但不知道多重特征群体的比例。

<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## 新建加权方案 <a href="#she-zhi-quan-zhong-ming-cheng" id="she-zhi-quan-zhong-ming-cheng"></a>

选择题目/变量（可选择1个或多个）->选择所需加权方案->设置目标权重百分比。

<figure><img src="../../.gitbook/assets/image (2) (2).png" alt=""><figcaption><p>功能入口</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (104).png" alt=""><figcaption><p>设置加权方案</p></figcaption></figure>

### 常规加权

常规加权即因子加权，根据一个条件或多个条件组合把答题用户划分为多个分组，并为每个分组设置对应目标比例（总计需为100%）。设置完成后，系统将根据目标占比和实际占比的数据，实时计算出每个用户分组的对应权重值。

<figure><img src="../../.gitbook/assets/image (5) (2).png" alt=""><figcaption><p>常规加权</p></figcaption></figure>

### 边缘加权

边缘加权适用于：需要调整采样群体以满足目标群体的代表，但不知道多重特征群体的比例的情况，一般有两个或以上的加权条件。设置完成后，系统将根据已设置的多个条件及对应目标占比进行迭代加权，以保证当前样本加权后符合多个条件的目标占比要求，精度为0.01%。

{% hint style="warning" %}
**特殊说明**

系统进行的迭代次数是有限的，当执行迭代次数超过25但当前样本加权后仍未同时满足多个条件的目标占比时，将自动结束迭代。如出现此情况，请增加投放样本或调整目标占比再重新执行加权。
{% endhint %}

<figure><img src="../../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>边缘加权</p></figcaption></figure>

## 应用1：在线统计 <a href="#yin-yong-quan-zhong" id="yin-yong-quan-zhong"></a>

统计图表页支持按权重方案查看各题统计结果。

<figure><img src="../../.gitbook/assets/image (1) (3).png" alt=""><figcaption><p>加权方案应用到统计图表</p></figcaption></figure>

支持选择多种加权方案，实时查看对比统计结果。

<figure><img src="../../.gitbook/assets/image (8) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>多种加权方案对比统计结果</p></figcaption></figure>

## 应用2：交叉分析

交叉分析功能支持按权重方案查看交叉结果。

<figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## 应用3：导出数据

设置并计算加权后，在“答题数据”-导出数据中，导出的答题数据明细包含每个样本对应的权重系数。可通过导出的明细数据进行其他深度分析。
