# Simple Logic

Simple logic: Control the display of specific questions or the end page jump based on the choices selected in the question. This is suitable for situations with a small number of questions or when the question has many choices. You can set different questions to be controlled by each choice.

Supports question types with simple logic settings: single choice , dropdown , multiple choice questions, scale , matrix single choice , matrix multiple choice , and matrix scale .

{% hint style="info" %}
1. Simple logic import is supported (only single-choice , multiple-choice and dropdown  logic import are supported). For the format, please refer to the "Survey Auto Import" section.
2. Questions set to display results are hidden by default and will only be shown when respondents select specified choices according to the logic settings.
3. Only one of simple logic or combinational logic functions can be used. Once combinational logic is enabled, simple logic can no longer be edited.
4. After enabling combinational logic, the system will automatically convert the set simple logic into combinational logic.
5. To set survey logic using "or" and "and" relationships, please switch to enable the combination logic feature.
{% endhint %}

## 【STEP 1】Set simple logic in the specified question

On the survey editing page, hover the mouse over the question that needs logic settings, and a simple logic setting button will appear on the right quick toolbar; or click the "Simple Logic" setting button on the right question settings bar in the question editing state to open the simple logic setting pop-up window.

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## 【STEP 2】Set Simple Logic (Control the Display of Questions)

In the simple logic setup popup, the left side contains the question choices, and the right side contains the list of all survey questions. Selecting an choice on the left and a question on the right indicates that the question on the right will be displayed only after the user selects the corresponding choice on the left; otherwise, the selected question on the right will not be displayed by default.

<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## 【STEP 3】Set Simple Logic (Control End Page)

By default, users answer questions in the default order of pages 1, 2, 3, etc. In the logic settings, it is supported to jump to the end page after selecting a specified choice according to the set logic (executed when the respondent clicks the next page; if there are other questions on the current page, the respondent needs to answer the other displayed questions).

{% hint style="info" %}
Default: Display the next page in the set default order

End page (normal end): After selecting the specified option, the respondent will jump to the end page when clicking the next page, and the survey data will be normally collected.

End page (abnormal termination, data not collection): After selecting the specified option, the respondent will be directed to the end page when clicking next, and the survey data will not be collected.
{% endhint %}

\


If clicking on the next page displays the end page (normal end), the survey will be marked as invalid and the status will be "invalid：jump to end page"\


<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
