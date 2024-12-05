# Data Cleaning

The system provides data cleaning functionality, applicable in scenarios where samples that do not meet specified criteria are removed after the survey is completed.[在线查看答题数据](../../../cao-zuo-zhi-yin/tong-ji-fen-xi/da-ti-shu-ju-zai-xian-cha-kan.md)/[导出数据](../../../cao-zuo-zhi-yin/xia-zai-shu-ju/)The disqualified samples are marked as invalid.

![Data Cleaning](<../../../.gitbook/assets/image (77).png>)

### 【STEP 1】Set Cleaning Conditions

On the "Statistics" - "Data Cleaning" page, click "Add Condition" in the top right corner to create a new cleaning condition.

### Create cleaning conditions

![Create cleaning conditions](<../../../.gitbook/assets/image (266).png>)

### The "and" and "or" relationships for setting conditions and rules

![Set cleaning rules](<../../../.gitbook/assets/image (786).png>)

{% hint style="info" %}
**Operation Tips**

When selecting multiple consecutive options in a dropdown list: click the first option -> hold down the shift key -> click the last option -> release the shift key to select all options in between.
{% endhint %}

![Set the and/or relationship between conditions (groups)](<../../../.gitbook/assets/image (76).png>)

\*\*Operational Tips\*\*

Support is provided for setting complex expression cleaning rules using conditions/condition groups, allowing nested conditions.

**Example:** To clean records where there is inconsistency about "sandbox game time":

Q9 "Sandbox game time" is selected as less than 5 hours

**and**

(Q10.1 A type sandbox game time is selected as more than 5 hours **or** Q10.2 B type sandbox game time is selected as more than 5 hours **or** Q10.3 C type sandbox game time is selected as more than 5 hours **or** Q10.4 D type sandbox game time is selected as more than 5 hours

![\[Example\] Complex Cleaning Conditions -- Nested Condition Group](<../../../.gitbook/assets/image (81).png>)

### 【STEP 2】Save and Execute Cleaning

After setting all the cleaning conditions, click on "Save Conditions" and "Execute Cleaning" in the upper right corner to trigger the cleaning task.

![保存条件](<../../../.gitbook/assets/image (623).png>)

{% hint style="warning" %}
The execution of cleaning must be done after the end of the deployment, and before triggering the cleaning, please make sure to "pause the recovery" first.
{% endhint %}

### 【STEP 3】View Data

After execution is complete, the page will display the number of invalid surveys removed for each condition.

![Cleaning completed](<../../../.gitbook/assets/image (217).png>)

Go to the[在线查看答题数据](../../../cao-zuo-zhi-yin/tong-ji-fen-xi/da-ti-shu-ju-zai-xian-cha-kan.md) ，You can view the survey responses marked as invalid.

![](<../../../.gitbook/assets/image (653).png>)
