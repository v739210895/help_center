# Weighted allocation

The system provides a weighted allocation function, applicable in scenarios where the number of respondents for certain types of surveys is insufficient or excessive, allowing the adjustment of the sample structure according to the desired target proportion.

Support two weight setting schemes

* Regular weighting (factor weighting): Assign target percentages for each response group totaling 100%
* Edge weighting: Also known as iterative proportional fitting or random iterative method. It is applicable in situations where you need to adjust the sampling population to meet the representation of the target population, but do not know the proportions of multiple characteristic groups.

<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### New Weighted Scheme

Select topic/variable (one or more) -> Choose the desired weighting scheme -> Set the target weight percentage.

<figure><img src="../../../.gitbook/assets/image (2) (2).png" alt=""><figcaption><p>Feature Entry</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (104).png" alt=""><figcaption><p>Set up weighting scheme</p></figcaption></figure>

### Regular weighting

Regular weighting, also known as factor weighting, divides respondents into multiple groups based on one or a combination of conditions and sets a corresponding target proportion for each group (totaling 100%). Once the setup is complete, the system will calculate the corresponding weight value for each user group in real-time based on the target proportion and actual proportion data.

<figure><img src="../../../.gitbook/assets/image (5) (2).png" alt=""><figcaption><p>常规加权</p></figcaption></figure>

### Edge Weighting

Edge weighting applies to situations where the sampling population needs to be adjusted to represent the target population, but the proportions of multiple feature groups are unknown. Typically, there are two or more weighting conditions. After the settings are completed, the system will perform iterative weighting based on the multiple conditions and corresponding target proportions that have been set, ensuring that the weighted current sample meets the target proportion requirements of multiple conditions, with an accuracy of 0.01%.

{% hint style="warning" %}
Special Instructions

The number of iterations performed by the system is limited. If the number of iterations exceeds 25 but the current weighted samples still do not meet the target proportion for multiple conditions simultaneously, the iteration will automatically end. If this occurs, please increase the sample size or adjust the target proportion and then re-execute the weighting.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1).png" alt=""><figcaption><p>Edge Weighting</p></figcaption></figure>

### Application 1: Online Statistics

The statistics chart page supports viewing the statistical results of each question according to the weighting scheme.

<figure><img src="../../../.gitbook/assets/image (1) (3).png" alt=""><figcaption><p>加权方案应用到统计图表</p></figcaption></figure>

Support multiple weighting schemes and view comparative statistics in real-time.

<figure><img src="../../../.gitbook/assets/image (8) (1) (1) (1).png" alt=""><figcaption><p>多种加权方案对比统计结果</p></figcaption></figure>

### Application 2: Cross Analysis

The cross-analysis feature supports viewing cross results based on the weighting scheme.

<figure><img src="../../../.gitbook/assets/image (6) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Application 3: Export Data

After setting and calculating the weights, the detailed answer data exported in the "Answer Data" - Export Data section includes the weight coefficient corresponding to each sample. Further in-depth analysis can be conducted using the exported detailed data.
