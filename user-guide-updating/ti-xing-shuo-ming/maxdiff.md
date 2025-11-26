# MaxDiff

MaxDiff (Maximum Difference Measurement) is an efficient preference measurement technique used to gauge people's preferences or perceptions of importance regarding a series of attributes. Unlike traditional rating scales, MaxDiff forces respondents to choose the "most preferred" and "least preferred" items in each set of options, thereby yielding more accurate and reliable data.

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## I. Core Advantages of MaxDiff

\
Eliminates Rating Bias: Avoids "score inflation" or "central tendency bias" commonly found in traditional rating scales.\
Enhances Discriminatory Power: Better distinguishes the relative importance of different attributes.\
Intuitive Results: Generates importance scores that are easy to understand and interpret.\
Cross-Cultural Applicability: Unaffected by differing cultural rating habits.

## II. Key Term Explanations

\
【Items】 In MaxDiff, the objects of comparison in the survey—such as brands, materials, styles, prices, etc.—are collectively referred to as "Items."\
【Task】 A set of attributes presented simultaneously for selecting the "best/worst" option. Each such set of questions is referred to as a "task." The number of tasks will be recommended based on the number of "Items" you input. You may manually adjust this number, but it must fall within the recommended range.\
【Number of Items per Task】 The quantity of "Items" displayed in each task.\
【Two-level Descriptions】 The descriptions corresponding to the choices for "attributes." For example, "most important"/"most likely" may describe the "best" option, while "least important"/"least likely" describe the "worst" option.\
【Random selection needed】 Indicates that each respondent does not need to evaluate all attributes. When enabled, attributes in each task are presented randomly, but the system ensures that each attribute appears an equal number of times as much as possible. This is suitable for surveys with a larger number of attributes.

## III. Setting Up MaxDiff in the Survey System

\
**Step 1: Create a MaxDiff** \
Go to the survey editing page and select "MaxDiff" from the list of question types.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Step 2: Edit the Question Stem and Select Bipolar Descriptions**\
The system offers six default recommended bipolar descriptions and supports customization.

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

**Step 3: Enter All Attributes (Attributes to Be Evaluated)**\
Input all the attributes that need to be evaluated. It is generally recommended to include at least 5 or more attributes.

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>



**Step 4: Configure Tasks (Design Scheme**)

\
1.Select the Number of items per Task\
This refers to how many items respondents will see in each selection task. It is recommended to show 3-5  items per task. Too many attributes may increase the difficulty of choice, while too few may reduce comparability.

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

2.Enter the Number of Tasks\
This refers to the total number of selection tasks a respondent needs to complete. The system will automatically recommend a reasonable range for the number of tasks based on the total number of attributes and the number of attributes per task. The survey can only be launched after the number of tasks has been manually entered.

<figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>



**3.**&#x52;andom selection needed (Optional)

When enabled, the system will randomly select N attributes for the respondent to evaluate. The attributes in each task are presented randomly, but the system ensures that each attribute appears an approximately equal number of times. This feature is suitable for studies with a large number of attributes.

<figure><img src="../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

4.Recommended minimum sample size = (500\*k)/(m\*t):

"k"is Total number of items

"m"is Number of items per task

"t"is Number of tasks

**Step 4: Preview and Publish**\
1.Click the "Preview" button to review the question display from the respondent's perspective and ensure all logic is correct.\
1.Once confirmed, click "Publish" to launch the survey.

**IV.Data Statistics**\
The system provides both basic reports and precision reports to assist with your analysis.

**1.Basic Report**

&#x20;The collected data is calculated in real-time, providing statistics on each attribute's preference share, score, number of times selected as most important, number of times selected as least important, and frequency of appearance.

<figure><img src="../../.gitbook/assets/image (1141).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Preference Share:** The preference share provides an intuitive visualization of the preference level or importance of each item. A higher value indicates a stronger preference for that item.

**Score：**&#x54;he scores reflect respondents' preference levels for the items.

A positive score indicates that the item was chosen as "best" more frequently than as "worst." A negative score indicates that the item was selected as "worst" more often than as "best."

Formula:(Number of times item chosen as best − Number of times chosen as worst) /Total number of times the item was presented
{% endhint %}

**2.Precision Report**

This feature requires more response data to be activated. It becomes available once the number of collected surveys exceeds 100.We will utilize a Multinomial Logit (MNL) model grounded in Random Utility Theory, which integrates "deterministic utility" and "random error components" to perform precise calculations for you. The extraction time for the report may vary depending on the volume of collected responses and the number of attributes included. Thank you for your patience.

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Preference Share:** This metric intuitively displays the preference level or importance of each item. A higher value indicates a stronger preference for the item. Calculation Logic: The system employs Maximum Likelihood Estimation (MLE) to fit a Multinomial Logit (MNL) model, maximizing the statistical probability of reproducing the actual sequence of choices you made. The model outputs utility coefficients (β values) for each attribute. These coefficients undergo exponential transformation (exp(β)) and are normalized to derive the Share of Preference (ranging from 0% to 100%). This method effectively mitigates scale bias inherent in traditional rating systems and is recognized as the international standard for preference measurement.

**Utility Value:** Represents the latent utility level of each option. A higher utility value indicates that the item is more important or attractive to users. Calculation Logic: Utility values are derived from a probabilistic choice model based on Random Utility Theory, estimated numerically through Maximum Likelihood Estimation (MLE) combined with the Newton-Raphson optimization algorithm.

**P Value:** Measures the statistical significance of preference for an item. A smaller p-value (typically < 0.05) indicates that the preference result is reliable and not due to random chance. Calculation Logic: The model calculates the probability of observing the extreme or more extreme data under the null hypothesis that the attribute has no effect (i.e., its true utility coefficient is zero). This probability is the p-value.
{% endhint %}

