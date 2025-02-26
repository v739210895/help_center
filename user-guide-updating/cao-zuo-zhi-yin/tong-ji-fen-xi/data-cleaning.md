# Data Cleaning

The system provides data cleaning functionality, applicable in scenarios where samples that do not meet specified criteria are removed after the survey is completed.[在线查看答题数据](../../../cao-zuo-zhi-yin/tong-ji-fen-xi/da-ti-shu-ju-zai-xian-cha-kan.md)/[导出数据](../../../cao-zuo-zhi-yin/xia-zai-shu-ju/)The disqualified samples are marked as invalid.

<figure><img src="../../../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>

### 【STEP 1】Set Cleaning Conditions

On the "Statistics" - "Data Cleaning" page, click "Add Condition" in the top right corner to create a new cleaning condition.

### Create cleaning conditions

<figure><img src="../../../.gitbook/assets/image (13) (1).png" alt=""><figcaption></figcaption></figure>

### The "and" and "or" relationships for setting conditions and rules

<figure><img src="../../../.gitbook/assets/image (15) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Operation Tips**

When selecting multiple consecutive options in a dropdown list: click the first option -> hold down the shift key -> click the last choice-> release the shift key to select all options in between.
{% endhint %}





### 【STEP 2】Save and Execute Cleaning

After setting all the cleaning conditions, click on "Save Conditions" and "Execute Cleaning" in the upper right corner to trigger the cleaning task.



<figure><img src="../../../.gitbook/assets/image (16) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
The execution of cleaning must be done after the end of the deployment, and before triggering the cleaning, please make sure to "pause the recovery" first.
{% endhint %}

### 【STEP 3】View Data

After execution is complete, the page will display the number of invalid surveys removed for each condition.

<figure><img src="../../../.gitbook/assets/image (17) (1).png" alt=""><figcaption></figcaption></figure>

Go to the[在线查看答题数据](../../../cao-zuo-zhi-yin/tong-ji-fen-xi/da-ti-shu-ju-zai-xian-cha-kan.md) ，You can view the survey responses marked as invalid.

<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>
