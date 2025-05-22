---
description: >-
  You can control the number of times a specified option is selected, and when
  the specified number is reached, the survey with this option selected will be
  marked as invalid due to quota. For example,
---

# Quota Settings

Quota settings only support single-choice , multiple-choice , and multi level linkage (requires address import)



### 【STEP 1】Choose single-channel or multi-channel distribute

For regular distribution, simply choose single-channel distribut(if you need to allocate quotas for multiple sub-links separately, you can choose multi-channel distribute）

<figure><img src="../../../.gitbook/assets/image (1086).png" alt=""><figcaption></figcaption></figure>

### 【STEP 2】Set Quota Question

Drag the items from the list on the left to the quota items on the right to create quota conditions.

<figure><img src="../../../.gitbook/assets/image (1087).png" alt=""><figcaption></figcaption></figure>

### 【STEP 3】Set quota quantity

Set the quota for each  choice with the default of 0 meaning no quota limit.

<figure><img src="../../../.gitbook/assets/image (1088).png" alt=""><figcaption></figcaption></figure>

### 【STEP 4】Turn on quota&#x20;

Before distributing the survey, please turn on the quota , otherwise the quota conditions will not be effective.

<figure><img src="../../../.gitbook/assets/image (1089).png" alt=""><figcaption></figcaption></figure>

### 【STEP5】Check quota progress

You can access the quota settings page at any time during the  distribute to check the quota progress.

<figure><img src="../../../.gitbook/assets/image (1090).png" alt=""><figcaption></figcaption></figure>

#### Set cross quotas <a href="#set-cross-quotas" id="set-cross-quotas"></a>

By setting cross quotas, you can limit the number of times options can be selected based on 2 questions. For example, if you need to collect 10 surveys from male players who like computer games, you can use cross quotas to accomplish this. Set it as shown in the figure below by dragging the questions from the list to the questions that need to participate in the cross quotas.

<figure><img src="../../../.gitbook/assets/23.gif" alt=""><figcaption></figcaption></figure>

### Maximum number of valid survey responses

When the number of valid surveys collected reaches the limit, the survey will automatically pause collection. The limit for valid surveys collected is 50,000.

<figure><img src="../../../.gitbook/assets/image (1091).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}


1. The two entries above have the same function. The upper one is commonly used for setting a single survey collection limit without setting any quota questions; the lower one is suitable for setting a survey collection limit while setting quotas for the questions.
2. A maximum limit for valid survey recovery can be set for each distribution channel. Once the limit is reached, the channel will automatically pause recovery, while other channels will continue to recover surveys normally.


{% endhint %}

### Advanced Features

\
Range quota

When conducting quantitative collection of some samples, certain users allow the collected samples to fluctuate within a certain range. For example, when collecting questions for males and females, the male ratio can be allowed to fluctuate between 80%-90% and the female ratio between 10%-20%. In this case, interval quotas can be used for control.

<figure><img src="../../../.gitbook/assets/image (1092).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
1. When using range quota, a limit for each question must be set. Once the limit for a question is reached, any choice selected for that question will be marked as having an invalid quota.
2. If the limit for a single question is not reached, when an choice reaches the maximum value of the range, selecting that choice will be marked as an invalid quota.
3. Interval quotas only apply to single-choice  in single-channel distribute.


{% endhint %}

#### Jump to the end page after quota is full

When the answerer clicks "next page", the system will determine whether the full quota of choices has been selected. If the quota is full, the system will automatically redirect to the end page without the need to complete all the questions.

<figure><img src="../../../.gitbook/assets/image (1093).png" alt=""><figcaption></figcaption></figure>

#### Add variable <a href="#add-variable" id="add-variable"></a>

Support custom variables, i.e., recombine question fields to generate new variables. The newly generated variables can participate in quotas or generate cross-quotas with other questions.

<figure><img src="../../../.gitbook/assets/image (1094).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (1095).png" alt=""><figcaption></figcaption></figure>

After successfully adding, a new variable question will be generated below the question list, and you can drag it to participate in the quota.

<figure><img src="../../../.gitbook/assets/image (1096).png" alt=""><figcaption></figcaption></figure>
