# Simple Logic

Simple logic: Control the display of specific questions or the end page jump based on the options selected in the question. This is suitable for situations with a small number of questions or when the question has many options. You can set different questions to be controlled by each option.

Supports question types with simple logic settings: single choice questions, dropdown questions, multiple choice questions, scale questions, matrix single choice questions, matrix multiple choice questions, and matrix scale questions.

{% hint style="info" %}
1. Simple logic import is supported (only single-choice questions, multiple-choice questions, and dropdown questions logic import are supported). For the format, please refer to the "Survey Auto Import" section.
2. Questions set to display results are hidden by default and will only be shown when respondents select specified options according to the logic settings.
3. Only one of simple logic or combinational logic functions can be used. Once combinational logic is enabled, simple logic can no longer be edited.
4. After enabling combinational logic, the system will automatically convert the set simple logic into combinational logic.
5. To set survey logic using "or" and "and" relationships, please switch to enable the combination logic feature.
{% endhint %}

## 【STEP 1】Set simple logic in the specified question

On the survey editing page, hover the mouse over the question that needs logic settings, and a simple logic setting button will appear on the right quick toolbar; or click the "Simple Logic" setting button on the right question settings bar in the question editing state to open the simple logic setting pop-up window.

![Quick Toolbar - Simple Logic](<../../../.gitbook/assets/image (102) (1).png>)

![Question Setup - Simple Logic](<../../../.gitbook/assets/image (565).png>)

## 【STEP 2】Set Simple Logic (Control the Display of Questions)

In the simple logic setup popup, the left side contains the question options, and the right side contains the list of all survey questions. Selecting an option on the left and a question on the right indicates that the question on the right will be displayed only after the user selects the corresponding option on the left; otherwise, the selected question on the right will not be displayed by default.

![Simple Logic Setup](<../../../.gitbook/assets/image (41).png>)

## 【STEP 3】Set Simple Logic (Control End Page)

By default, users answer questions in the default order of pages 1, 2, 3, etc. In the logic settings, it is supported to jump to the end page after selecting a specified option according to the set logic (executed when the respondent clicks the next page; if there are other questions on the current page, the respondent needs to answer the other displayed questions).

{% hint style="info" %}
Default: Display the next page in the set default order

End page (normal end): After selecting the specified option, the respondent will jump to the end page when clicking the next page, and the survey data will be normally collected.

End page (abnormal termination, data not collected): After selecting the specified option, the respondent will be directed to the end page when clicking next, and the survey data will not be collected.
{% endhint %}

![Simple Logic Setup](<../../../.gitbook/assets/image (634).png>)
