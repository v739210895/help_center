# Combinational Logic

The rules of combinational logic are as follows: This question is hidden by default and will only be displayed when the set conditions are met (e.g., selecting option A in Q2). It supports setting an end page (data collected) and an end page (data not collected) as display results: When the specified conditions are met (e.g., selecting option A in Q2), the respondent will be directed to the end page after clicking the next page button.

## 【STEP 1】New logic added

Switch to the "Combined Logic" function on the survey editing page, and click the "New Logic" button to create a new rule.

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>



## 【STEP 2】Set display results

In the newly created combination logic rules, you need to first set the display result question. In the pop-up window, specify the display result as a question, end page (normal end), or end page (abnormal end, data not collected).

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

### （1）Set the end page to display results

When the specified conditions are met, the respondent will be redirected to the end page upon clicking the next page button on that page.

{% hint style="info" %}
1、The end page (normal end) and the end page (abnormal end, no data collection) can only be set to display the results once. If you need to control the end page with multiple conditions, please use logical relationships such as "or" and "and". &#x20;

&#x20;      eg：After Rule 1 sets the end page (normal end) as the result display, Rule 2 can no longer set the end page (normal end) as the result display.

2、End page (abnormal end, data not collected) means that when the respondent meets the specified conditions and clicks the next page button on this page, they will be directed to the end page, and the response data will not be collected.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

### （2）Set the question to display results

When the specified conditions are met after setting, the specified question(s) will be displayed. You can specify one or more questions.。

{% hint style="info" %}
Each question can only be set to display results once. If Rule 1 sets Q2 to display results, Rule 2 cannot set Q2 to display results again.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

### Display on the page after setting the results

Click OK in the display results popup to show it in the logic settings.

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Click the "Set Display Result" button in this rule again to modify the already set display result.

## 【STEP 3】Set display conditions

Set the display conditions for the combination logic rules, including the questions and specific conditions. After clicking "Set Conditions," select the question, condition (selected/unselected/display), and options in the popup window.

{% hint style="info" %}
Single choice questions, multiple choice questions, dropdown questions, scale questions, and matrix single choice questions can have conditions set, including whether the question is displayed and whether specified options are selected or not selected.

Subjective questions, information fields, and linked questions can have conditions set, including whether the question is displayed.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

After clicking confirm, the system will generate multiple rules based on the selected conditions, such as Q1 option A selected, Q1 option B selected, Q2 displayed, Q3 option C not selected, etc., and display them on the logic settings page.

![](<../../../.gitbook/assets/image (642).png>)

Click the "Set Conditions" button in this rule again to modify the rule.

## 【STEP 4】Set Conditional Logic

If multiple conditions are set in \[STEP 3], the default is to display the question results when any one condition is met. After selecting the "Custom Conditions" function in the rules, you can freely define logical expressions by connecting conditions with: and, or, and parentheses (defining the logical relationship of multiple added conditions). When the conditions are met, the result question will be displayed.

![](<../../../.gitbook/assets/image (67).png>)

![](<../../../.gitbook/assets/image (507).png>)

{% hint style="danger" %}
### 【Conditional Logic Explanation】

or Indicates or relationship

and Representation and Relationship

( ) Indicating binding calculation

Separate conditional numbers and the and/or operators with spaces, and the operators only support lowercase English.
{% endhint %}

Example：1 and 2 and (3 or 4)&#x20;

## 【STEP 5】Delete logic

Click the delete button at the top right corner of the specified rule to delete this rule.

![](<../../../.gitbook/assets/image (473).png>)

## 【STEP 6】Save current settings

After the logic is set up, click the "Save" button in the upper right corner to save and apply all the rules on the current page. (Surveys that are being collected do not support modification and saving. If you need to modify the rules, please pause the collection first.)

![](<../../../.gitbook/assets/image (590).png>)

### Frequently Asked Questions

### Can the logic settings span across pages?

Yes, it is possible.

If the display result questions and conditional questions in the logic settings are all set on one page, it will cause the result questions to be continuously displayed (popping up), affecting the user's visual experience and the smoothness of answering the survey. It is recommended to set the display logic across pages as much as possible, to avoid making external users feel that the questions are constantly changing.



### Why can't the questions be set with combined logic?

Each question can only be set as the display result of a combination logic once. If it has already been set as the display result of a combination logic, the original rule must be deleted before it can be set again.



### Why does my survey show a blank page?

A blank page usually appears because all the questions on that page are set as the display result of combined logic questions, and are hidden by default. Please carefully review the user’s answering path to ensure that every path is clear and unobstructed.



