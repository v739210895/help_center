---
hidden: true
---

# Conjoint

Conjoint  simulates real purchasing decision scenarios by allowing respondents to choose and weigh complete product concepts composed of different attributes (such as price, features, design) and their levels. The core purpose of this approach is to quantify consumer preferences for various product features. Ultimately, through statistical models, it derives the utility value and relative importance of each attribute level in overall choice.

#### 一、Core Advantages of Conjoint <a href="#yi-maxdiff-de-he-xin-you-shi" id="yi-maxdiff-de-he-xin-you-shi"></a>

* Restoring Multi-Attribute Trade-offs: Simulating the Multi-Factor Trade-off Process Faced by Consumers in Actual Purchases  \

* Closer to Reality Choices: Closer to Decision-Making Behavior in the Real Market than Individual Ratings
* Highly predictive: Able to predict market acceptance of new product configurations

#### **二、 关键词说明** <a href="#er-guan-jian-ci-shuo-ming" id="er-guan-jian-ci-shuo-ming"></a>

\[Attributes] refer to the characteristics or dimensions of a product or service that can be evaluated by consumers. For example, in the case of a "laptop," its attributes may include "brand," "price," "screen size," "memory," and "hard drive capacity."

\[Level] refers to the levels (attribute values) under an attribute, for example, the levels of the brand: Lenovo, HP...; the levels of memory: 8G, 16G...;

\[Concept] It is a complete and virtual product description composed of selecting one level from each attribute. For example, HP-i5-15 inch-16G-6000 is referred to as a concept.

\[Task] Extract several "concepts" and display them simultaneously, requiring respondents to evaluate all the "concepts" presented. Each set of such questions is referred to as a task.

"Number of Concepts per Task" refers to the number of "concepts" presented to respondents simultaneously in one "task." It is recommended to present 2-5 concepts per task because when the number of concepts exceeds 5, it becomes difficult for respondents to accurately select the most appealing concept.

\[Concept Type]

System Random Combination Concept: The system will randomly combine attributes and levels edited by the user into concepts and present them to the user for evaluation. The system will strive to ensure that each concept appears with equal frequency to ensure the accuracy of the survey data.

Custom Concept: Users can upload custom combinations of multi-attribute and multi-level concepts without the need for the system to combine them. Users need to fill in the attributes and levels of the custom concept according to the template before uploading. This is suitable for scenarios with fixed evaluation concept combinations.

{% hint style="info" %}
Simply put, these nouns form the design framework for conjoint analysis:\
Researchers first define the attributes and levels of the study, which the system uses to combine into multiple complete concepts, or custom concepts can be uploaded. In the questionnaire, each question is a task, and each task will include specific concepts for respondents to evaluate.
{% endhint %}

#### 三、如何在问卷系统中使用联合分析题 <a href="#san-wen-juan-xi-tong-zhong-she-zhi-maxdiff-ti" id="san-wen-juan-xi-tong-zhong-she-zhi-maxdiff-ti"></a>

**第一步：创建联合分析题型**

进入问卷编辑页面，在题型列表中选择 “联合分析”

![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252FawCWQxwXFuQ2QGH4WTp1%252Fimage.png%3Falt%3Dmedia%26token%3Dd5ee63e6-0611-43c5-8e4d-896a912d57be\&width=768\&dpr=4\&quality=100\&sign=a0e68ca\&sv=2)

**第二步：右侧题目设置选择概念类型**

**系统随机组合概念：** 系统会根据用户编辑的属性与水平随机组合成概念呈现给用户测评，系统会尽量保证每个概念出现频次均等来确保调研数据的准确性。

* 编辑属性与水平



**自定义概念：** 用户自定义组合“多属性多水平概念后进行上传，无需系统做组合，需按模板示意将自定义概念的属性、水平对应填充后上传。适用于已有固定测评的概念组合场景。

* 上传自定义概念



**第三步：配置任务（设计方案）**

1.  选择每个任务概念数

    * 指受访者在每一次选择中会看到多少个概念。建议2\~5个，数量过多会增加选择难度，过少缺少对比性

    ![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252FeyLkAnqjEI8qsT6QxomI%252Fimage.png%3Falt%3Dmedia%26token%3Dc66b334f-f164-44e4-a816-bddda954179c\&width=768\&dpr=4\&quality=100\&sign=94b3208f\&sv=2)
2.  输入任务数

    * 指一位受访者总共需要完成多少次选择任务。系统会根根据概念自动推荐一个合理任务数范围，需手动输入任务数后才可投放

    ![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252Fh0HWH9i0RilnQQTkl90Z%252Fimage.png%3Falt%3Dmedia%26token%3Df9c0501d-af07-46cf-916b-b692f6f11d74\&width=768\&dpr=4\&quality=100\&sign=9651477f\&sv=2)
3. 每个任务包含空选项（可选）

* 在每个概念中增加一个空选项，用于模拟真实决策场景--以上概念我都不想选择

![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252FqxRcC5YPRX02VWmbTNci%252Fimage.png%3Falt%3Dmedia%26token%3D4517750e-1c05-43ca-8e70-9f4fbef49f07\&width=768\&dpr=4\&quality=100\&sign=d9998abb\&sv=2)



**第四步：预览与发布**

1. 点击 “预览” 按钮，以作答者者视角检查题目展示效果，确保逻辑无误。
2. 确认无误后，“发布” 问卷。

#### 四、数据统计 <a href="#si-shu-ju-tong-ji" id="si-shu-ju-tong-ji"></a>

提供基础报告与精准报告辅助您分析

![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252FikitAtWbFJrEha5LaeTI%252Fimage.png%3Falt%3Dmedia%26token%3Dd3050bcc-cf00-4f87-b1ac-41a9ef0536be\&width=768\&dpr=4\&quality=100\&sign=84f4bfd9\&sv=2)

**1.基础报告**

回收数据实时计算，统计每个概念出现次数、被选中次数、分数

![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252FUOrqS1mQNSQmlyGNemB7%252Fimage.png%3Falt%3Dmedia%26token%3D0576fb41-652a-47d5-9532-ff34aa70658c\&width=768\&dpr=4\&quality=100\&sign=28859987\&sv=2)

{% hint style="info" %}
**分数：**&#x5206;数反映了受访者对概念的偏好程度。分数越高代表在所有概念中更受欢迎。

计算公式：被选中次数 / 出现的总次数&#x20;
{% endhint %}

&#x20;           &#x20;

**2.精准报告**

我们将采用分层贝叶斯（HB）模型与MCMC（Metropolis-Hastings）算法，通过个体级参数估计与群体分布的先验约束，在贝叶斯框架下同步拟合所有受访者的效用值。该计算方法能有效处理稀疏选择数据并提升小样本估计效率

![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252FX2PXzBw0Y5HWmB62pfdz%252Fimage.png%3Falt%3Dmedia%26token%3D72ea55f8-7a3e-472d-bf73-b398a0a39c20\&width=768\&dpr=4\&quality=100\&sign=1cd2dffa\&sv=2)



{% hint style="success" %}
**属性重要性：**&#x91CD;要性越大，表示该属性对受访者越重要。计算公式：属性重要性=（属性效用值范围/所有属性效用值范围）\*100%

**水平效用值：**&#x6BCF;个水平的潜在效用，效用值越高，代表该水平在用户心目中越重要、越有吸引力。计算逻辑：基于分层贝叶斯框架下的随机效用理论，通过MCMC（Metropolis-Hastings）算法对个体与群体层面的后验分布进行迭代抽样，从而估算出各属性水平的效用值。

**概念效用值：**&#x6BCF;个概念的潜在效用，效用值越高，代表该概念在用户心目中越重要、越有  吸引力。计算逻辑：构成该概念的所有属性水平的效用值累加得出
{% endhint %}



