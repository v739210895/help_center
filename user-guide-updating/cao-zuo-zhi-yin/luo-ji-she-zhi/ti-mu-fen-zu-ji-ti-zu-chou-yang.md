# Grouping of Questions and Sampling of Question Sets

The survey system supports grouping survey questions, dividing the questions into multiple question groups. After grouping, you can set the conditions for displaying specific question groups in the "combination logic". The question group will only be displayed if the conditions are met. You can also set random sampling for the question groups, meaning that n questions will be randomly sampled and displayed from the groups that meet the display conditions, reducing the number of questions the respondent needs to answer.

### Question Grouping

### STEP 1 Add Group

In "Logic" - "Question Grouping", click "Add Group" in the top right corner to create a new question group.

![Add Group](<../../../.gitbook/assets/image (586).png>)

![Name groups of questions](<../../../.gitbook/assets/image (245).png>)

### STEP 2 Move the question into the group

Check the questions in the "Question Outline" on the left, then click the ">" button on the left side of the group you want to move them to. The questions will be assigned to the specified group.

{% hint style="info" %}
1. A question can only be assigned to one group.
2. Matrix single-choice questions/matrix multiple-choice questions/matrix scale questions can only be grouped as a whole.
3. Support displaying only grouped survey questions in a fixed order, while ungrouped questions are displayed in a fixed sequence.
4. For questions within/outside the question group, the logic settings still apply. The questions will only be displayed if the logic conditions are met.
{% endhint %}

![Move the specified question into the group](<../../../.gitbook/assets/image (324).png>)

![Complete the grouping by topic](<../../../.gitbook/assets/image (152).png>)

### STEP 3 Grouping completed, save

After dividing the required items into multiple groups as per Step 2, click "Save" in the top

![Final Grouping Results](<../../../.gitbook/assets/image (2) (1) (1) (1) (1).png>)



### Cluster random sampling

After grouping the questions, it supports setting a random sampling number for the questions. A specified number of questions will be randomly selected from the question groups that meet the display conditions. If the number of question groups that meet the display conditions is less than the set random sampling number, all questions that meet the conditions will be displayed.

The sampling mechanism is automatically performed by the system. As the number of survey responses increases, the distribution of each sample group becomes more even.

![Cluster random sampling](<../../../.gitbook/assets/image (122).png>)

\*\*Special Instructions\*\*

To prevent respondents from refreshing the survey multiple times to guess questions, the system has certain limitations on the sampling mechanism: questions will appear relatively consistently for the same cookie information.

(Example: If Player A uses QQ browser to fill out the survey, the system shows question set 3. If Player A opens the survey again using the same browser, the system will still show question set 3 to them.)

To test and check the question sampling, please switch browsers or clear the current browser's cookie information after each attempt.&#x20;



### Question set logic

In "combination logic," you can set logical display conditions for specified question groups. Only when these conditions are met will the specified question groups be displayed normally or enter the random sampling range.

![Set the question group to display results](<../../../.gitbook/assets/image (375).png>)

![Question set logic](<../../../.gitbook/assets/image (723).png>)



