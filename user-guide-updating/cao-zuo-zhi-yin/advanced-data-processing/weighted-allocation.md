# Weighted allocation

The system provides a weighted allocation function, applicable in scenarios where the number of respondents for certain types of surveys is insufficient or excessive, allowing the adjustment of the sample structure according to the desired target proportion.

Support two weight setting schemes

* Regular weighting (factor weighting): Assign target percentages for each response group totaling 100%
* Edge weighting: Also known as iterative proportional fitting or random iterative method. It is applicable in situations where you need to adjust the sampling population to meet the representation of the target population, but do not know the proportions of multiple characteristic groups.
*

    <figure><img src="../../../.gitbook/assets/image (1008).png" alt=""><figcaption></figcaption></figure>

### New Weighted Scheme

Select topic/variable (one or more) -> Choose the desired weighting scheme -> Set the target weight percentage.

<figure><img src="../../../.gitbook/assets/image (1009).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (1010).png" alt=""><figcaption></figcaption></figure>

### Regular weighting

Regular weighting, also known as factor weighting, divides respondents into multiple groups based on one or a combination of conditions and sets a corresponding target proportion for each group (totaling 100%). Once the setup is complete, the system will calculate the corresponding weight value for each user group in real-time based on the target proportion and actual proportion data.

<figure><img src="../../../.gitbook/assets/image (5) (2).png" alt=""><figcaption><p>Regular weighting</p></figcaption></figure>

### Edge Weighting

Edge weighting applies to situations where the sampling population needs to be adjusted to represent the target population, but the proportions of multiple feature groups are unknown. Typically, there are two or more weighting conditions. After the settings are completed, the system will perform iterative weighting based on the multiple conditions and corresponding target proportions that have been set, ensuring that the weighted current sample meets the target proportion requirements of multiple conditions, with an accuracy of 0.01%.

{% hint style="warning" %}
Special Instructions

The number of iterations performed by the system is limited. If the number of iterations exceeds 25 but the current weighted samples still do not meet the target proportion for multiple conditions simultaneously, the iteration will automatically end. If this occurs, please increase the sample size or adjust the target proportion and then re-execute the weighting.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Edge Weighting</p></figcaption></figure>

###
