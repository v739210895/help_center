# Data Cleaning

The system provides data cleaning functions, applicable scenarios: after the survey is completed, samples that do not meet the specified conditions will be removed. Unqualified samples will be marked as invalid and will not participate in statistics and cross-calculations.

## 【STEP 1】Set Cleaning Conditions

On the "Data Processing" - "Data Cleaning" page, click "Add Condition" in the upper right corner to create a new cleaning condition.

<figure><img src="../../../.gitbook/assets/image (11) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Type 1: Regular Cleaning

<figure><img src="../../../.gitbook/assets/image (12) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Operation Tips**

When selecting options, if you need to select multiple consecutive options, follow these steps in the dropdown list: click the first option -> hold down the shift key -> click the last option, release the shift key, and the consecutive selection will be made.
{% endhint %}

### The "and" and "or" relationships for setting conditions and rules

\*\*Operation Tip\*\*

You can set up complex cleaning rules using conditions or condition groups, allowing for nested conditions.

<mark style="color:red;">【Example】</mark> To clean up inconsistent responses regarding "Sandbox Game Time":

Q9 Sandbox Game Time selected less than 5 hours

**and**

(Q10.1 Type A Sandbox Game Time selected options for more than 5 hours

**or** Q10.2 Type B Sandbox Game Time selected options for more than 5 hours

**or** Q10.3 Type C Sandbox Game Time selected options for more than 5 hours

**or** Q10.4 Type D Sandbox Game Time selected options for more than 5 hours

Type 2: Smart Cleaning

The system supports intelligent cleaning of matrix single-choice, matrix multiple-choice, and matrix scale questions. If a player selects the same option for all sub-questions in a matrix question, the survey will be considered as a random fill-in, and the system will mark the survey as "invalid".

<figure><img src="../../../.gitbook/assets/image (13) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Explanation of the Cleaning Mechanism**

Smart cleaning will judge based on the answers submitted by the player in this matrix question. If the player submits identical answers for multiple sub-questions in this matrix question, the response will be considered invalid.&#x20;


{% endhint %}

## 【STEP 2】Save and execute cleaning

After setting all the cleaning conditions, click "Save Conditions" and "Execute Cleaning" in the upper right corner to trigger the cleaning task.

<figure><img src="../../../.gitbook/assets/image (14) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## 【STEP 3】View data

After execution is completed, the page will display the number of invalid surveys removed for each condition. Surveys marked as invalid will not be included in export, statistics, or cross-analysis.。

<figure><img src="../../../.gitbook/assets/image (15) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Go to "Survey Data" to view the responses marked as invalid.

<figure><img src="../../../.gitbook/assets/image (16) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
