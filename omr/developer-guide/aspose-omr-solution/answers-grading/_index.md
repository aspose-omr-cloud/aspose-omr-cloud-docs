---
title: "Answers Grading"
type: docs
url: /answers-grading/
weight: 60
---

## **Overview**
GradeAnswers function allows you to grade OMR answers based on provided rules. This function takes simple input: recognition results and JSON rules, which are highly customizable. As a result, you receive a detailed response with total grades and info about each question.
## **How To**
**Step 1. Provide answers you would like to grade in the .dat file**

It has a very simple structure, see example below:

**MyTest.dat**

```java

Question1: A

Question2: D

Question3: C

Question4: EB

Question5: D

Question6: C

Question7:

Question8: B

Question9: C

Question10:

```

**Step 2. Provide JSON string with rules that will be used to grade answers**

**MyRules**

```java

{

  "Pages": [

    {

      "PageId": 12345,

      "CorrectPoints": 5,

      "IncorrectPoints": 2,

      "EmptyPoints": 1,

      "IncompleteAnswerPoints": 0.5,

      "IncompleteAnswersAllowed": true,

      "QuestionRules": [

        {

          "QuestionName": "Question1",

          "ToGrade": true,

          "Answer": "A",

          "CorrectPoints": 4

        },

        {

          "QuestionName": "Question2",

          "ToGrade": true,

          "Answer": "D"

        },

        {

          "QuestionName": "Question3",

          "ToGrade": true,

          "Answer": "C"

        },

        {

          "QuestionName": "Question4",

          "ToGrade": true,

          "Answer": "BE"

        },

        {

          "QuestionName": "Question5",

          "ToGrade": true,

          "Answer": "ED"

        },

        {

          "QuestionName": "Question6",

          "ToGrade": true,

          "Answer": "C"

        },

        {

          "QuestionName": "Question7",

          "ToGrade": true,

          "Answer": "A"

        },

        {

          "QuestionName": "Question8",

          "ToGrade": true,

          "Answer": "B"

        },

        {

          "QuestionName": "Question9",

          "ToGrade": true,

          "Answer": "D"

        },

        {

          "QuestionName": "Question10",

          "ToGrade": true,

          "Answer": "C",

          "EmptyPoints": 3

        }

      ]

    }

  ]

}

```

**JSON Rules can be divided into two parts: Header and Questions**

**1. Header**

Rules description starts with the header, which contains several properties that are applied to all graded questions. 

These properties are:

|**Property**|**Description**|**Example**|
| :- | :- | :- |
|CorrectPoints|Points for correct answer.|1 <br>3.5|
|IncorrectPoints|Points for an incorrect answer.|0 <br>0.5|
|EmptyPoints|Points for an empty answer, i.e. no answer provided.|0 <br>0.1|
|IncompleteAnswerPoints|Points for a partially correct answer in the multi-select question. Points are awarded for each correct answer key. <br>For example, let the answer be ABD, the correct answer is BDE and IncompleteAnswerPoints equals 1. Then two keys are correct and 2 points will be awarded. <br>Also, each missed answer key is awarded IncorrectPoints.|0 <br>0.5|
|IncompleteAnswersAllowed|Boolean value indicating whether IncompleteAnswerPoints has to be awarded for the partially correct answers. If this value is false, only fully correct answers are taken into account.|false <br>true|
**2. Questions**

The second part is a JSON array that contains information about each question that needs to be graded. Each question has 3 required properties that are critical for the grading:

|**Property**|**Description**|**Example**|
| :- | :- | :- |
|QuestionName|Name of the question|"Question1"|
|ToGrade|Boolean value indicating whether this question has to be graded. You can avoid grading specific questions settings this value to false.|true <br>false|
|Answer|String representing correct answer for the question. This is the value that compared to the provided answer key.|"A" <br>"cd" <br>"8"|
```java

{

    "QuestionName": "Question2",

    "ToGrade": true,

    "Answer": "D"

}

```

**Question Rules Customization**

In case you want to customize specific question, you can provide additional properties in the question section. These "local" properties will have higher priority over general rules. In such a way, you can "overwrite" rules for a specific question. Properties that you can overwrite are **CorrectPoints, IncorrectPoints, EmptyPoints, IncompleteAnswerPoints**. See example below with set rules for specific question:

```java

{

    "QuestionName": "Question1",

    "ToGrade": true,

    "Answer": "A",

    "CorrectPoints": 4,

    "IncorrectPoints": 1,

    "EmptyPoints": 0.5,

    "IncompleteAnswerPoints": 0

}

```

**Step 3. Call GradeAnswers OMR function and provide all the parameters**

See C# example below: 

{{< gist "aspose-cloud" "b0e9305b5be4b21598cfdd5dd21102cb" "Examples-.NET-GradeAnswers-OMR-Function.cs" >}}

**Step 4. Get Grades**

The response contains a single **.rule** file and has the following structure:

**MyTestResults.grade**

```java

{

  "Pages": [

    {

      "PageId": 12345,

      "TotalPoints": 35.5,

      "MaxPossiblePoints": 49,

      "GradedQuestions": 10,

      "QuestionGrades": [

        {

          "QuestionName": "Question1",

          "Points": 4,

          "Response": "A",

          "CorrectAnswer": "A",

          "IsCorrect": true

        },

        {

          "QuestionName": "Question2",

          "Points": 5,

          "Response": "D",

          "CorrectAnswer": "D",

          "IsCorrect": true

        },

        {

          "QuestionName": "Question3",

          "Points": 5,

          "Response": "C",

          "CorrectAnswer": "C",

          "IsCorrect": true

        },

        {

          "QuestionName": "Question4",

          "Points": 5,

          "Response": "EB",

          "CorrectAnswer": "BE",

          "IsCorrect": true

        },

        {

          "QuestionName": "Question5",

          "Points": 0.5,

          "Response": "D",

          "CorrectAnswer": "ED",

          "IsCorrect": false

        },

        {

          "QuestionName": "Question6",

          "Points": 5,

          "Response": "C",

          "CorrectAnswer": "C",

          "IsCorrect": true

        },

        {

          "QuestionName": "Question7",

          "Points": 1,

          "Response": "",

          "CorrectAnswer": "A",

          "IsCorrect": false

        },

        {

          "QuestionName": "Question8",

          "Points": 5,

          "Response": "B",

          "CorrectAnswer": "B",

          "IsCorrect": true

        },

        {

          "QuestionName": "Question9",

          "Points": 2,

          "Response": "C",

          "CorrectAnswer": "D",

          "IsCorrect": false

        },

        {

          "QuestionName": "Question10",

          "Points": 3,

          "Response": "",

          "CorrectAnswer": "C",

          "IsCorrect": false

        }

      ]

    }

  ]

}

```
