---
hidden: true
---

# Conjoint

Conjoint  simulates real purchasing decision scenarios by allowing respondents to choose and weigh complete product concepts composed of different attributes (such as price, features, design) and their levels. The core purpose of this approach is to quantify consumer preferences for various product features. Ultimately, through statistical models, it derives the utility value and relative importance of each attribute level in overall choice.

#### 一、Core Advantages of Conjoint <a href="#yi-maxdiff-de-he-xin-you-shi" id="yi-maxdiff-de-he-xin-you-shi"></a>

* Restoring Multi-Attribute Trade-offs: Simulating the Multi-Factor Trade-off Process Faced by Consumers in Actual Purchases  \

* Closer to Reality Choices: Closer to Decision-Making Behavior in the Real Market than Individual Ratings
* Highly predictive: Able to predict market acceptance of new product configurations

#### **二、** Key Term Explanations <a href="#er-guan-jian-ci-shuo-ming" id="er-guan-jian-ci-shuo-ming"></a>

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

#### 三、How to Use Conjoint Analysis Questions in a Survey System <a href="#san-wen-juan-xi-tong-zhong-she-zhi-maxdiff-ti" id="san-wen-juan-xi-tong-zhong-she-zhi-maxdiff-ti"></a>

**Step 1: Create a conjoint**

Enter the questionnaire editing page and select "Conjoint " from the question type list.

![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252FawCWQxwXFuQ2QGH4WTp1%252Fimage.png%3Falt%3Dmedia%26token%3Dd5ee63e6-0611-43c5-8e4d-896a912d57be\&width=768\&dpr=4\&quality=100\&sign=a0e68ca\&sv=2)

**Step 2: Select the concept type in the question settings on the right side.**

**System Random Combination Concept:** The system will randomly combine concepts based on the attributes and levels edited by the user and present them for user evaluation. The system will strive to ensure that each concept appears with equal frequency to ensure the accuracy of the survey data.

* Edit Attributes and Levels



**Custom Concept:** Users can upload their custom combinations of multi-attribute and multi-level concepts without the system needing to do the combinations. Users need to fill in the attributes and levels of the custom concept according to the template before uploading. This is suitable for scenarios with fixed concept combinations for evaluations.

* Upload Custom Concept



**Step 3: Configure Tasks (Design Plan)**

1.  Select the number of concepts for each task

    * This refers to how many concepts respondents will see in each selection. It is recommended to have 2 to 5 concepts; too many will increase the difficulty of selection, while too few will lack comparability.

    ![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252FeyLkAnqjEI8qsT6QxomI%252Fimage.png%3Falt%3Dmedia%26token%3Dc66b334f-f164-44e4-a816-bddda954179c\&width=768\&dpr=4\&quality=100\&sign=94b3208f\&sv=2)
2.  Enter the number of tasks

    * Refers to the total number of choice tasks a respondent needs to complete. The system will automatically recommend a reasonable range of task numbers based on the concept, and the task number must be manually entered before it can be launched.

    ![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252Fh0HWH9i0RilnQQTkl90Z%252Fimage.png%3Falt%3Dmedia%26token%3Df9c0501d-af07-46cf-916b-b692f6f11d74\&width=768\&dpr=4\&quality=100\&sign=9651477f\&sv=2)
3. Each task includes an empty option (optional)

* Add a blank option to each concept to simulate a real decision-making scenario -- I don't want to choose any of the above concepts.

![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252FqxRcC5YPRX02VWmbTNci%252Fimage.png%3Falt%3Dmedia%26token%3D4517750e-1c05-43ca-8e70-9f4fbef49f07\&width=768\&dpr=4\&quality=100\&sign=d9998abb\&sv=2)



**Step 4: Preview and Publish**

1. Click the "Preview" button to check the display effect of the question from the perspective of the respondent to ensure the logic is correct.
2. After confirming no errors, "publish" the questionnaire.

#### 四、Data Statistics <a href="#si-shu-ju-tong-ji" id="si-shu-ju-tong-ji"></a>

Provide basic reports and accurate reports to assist you in analysis.

![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252FikitAtWbFJrEha5LaeTI%252Fimage.png%3Falt%3Dmedia%26token%3Dd3050bcc-cf00-4f87-b1ac-41a9ef0536be\&width=768\&dpr=4\&quality=100\&sign=84f4bfd9\&sv=2)

**1.Basic Report**

Real-time calculation of recycling data, counting the number of occurrences, selections, and scores for each concept.

![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252FUOrqS1mQNSQmlyGNemB7%252Fimage.png%3Falt%3Dmedia%26token%3D0576fb41-652a-47d5-9532-ff34aa70658c\&width=768\&dpr=4\&quality=100\&sign=28859987\&sv=2)

{% hint style="info" %}
Score: The score reflects the respondents' preference level for the concept. A higher score indicates greater popularity among all concepts.\
Calculation formula: Number of times selected / Total number of occurrences
{% endhint %}

&#x20;           &#x20;

**2.**&#x41;ccurate Report

We will use a Hierarchical Bayesian (HB) model with the MCMC (Metropolis-Hastings) algorithm to simultaneously fit all respondents' utility values within a Bayesian framework through individual-level parameter estimation and prior constraints of the population distribution. This computational method can effectively handle sparse choice data and enhance estimation efficiency for small samples.

![](https://imur.gitbook.io/help_center/~gitbook/image?url=https%3A%2F%2F1246225111-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Lnu1UZ4dgrL0WcgooHk%252Fuploads%252FX2PXzBw0Y5HWmB62pfdz%252Fimage.png%3Falt%3Dmedia%26token%3D72ea55f8-7a3e-472d-bf73-b398a0a39c20\&width=768\&dpr=4\&quality=100\&sign=1cd2dffa\&sv=2)



{% hint style="success" %}
**Attribute Importance:** The greater the importance, the more important the attribute is to the respondents. Calculation formula: Attribute Importance = (Range of Attribute Utility Value / Range of All Attribute Utility Values) \* 100%

**Level utility value:** The potential utility of each level, where a higher utility value indicates that the level is more important and attractive in the user's mind. Calculation logic: Based on the random utility theory under a hierarchical Bayesian framework, the Metropolis-Hastings (MCMC) algorithm is used to perform iterative sampling on the posterior distribution at both individual and group levels, thereby estimating the utility values of each attribute level.

**Concept Utility Value:** The potential utility of each concept. The higher the utility value, the more important and attractive the concept is perceived by users. Calculation Logic: The utility values of all attribute levels that constitute the concept are summed up to derive it.
{% endhint %}



