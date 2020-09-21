---
title: "OMR API Specification"
type: docs
url: /omr-api-specification/
weight: 20
---

## **Function Specifications**
At present, Aspose.OMR for Cloud API exposes single function with string parameter that determines which specific action should be performed.

{{< gist "aspose-cloud" "b0e9305b5be4b21598cfdd5dd21102cb" "Examples-.NET-PostRunOmrTask.cs" >}}
### **OMRFunctionParam Description**
**OMRFunctionParam** is a separate class that has **FunctionParam** property. This property accepts string parameters, usually JSON strings, that are specific to each action. See examples given below for each action.

|**Property Name**|**Type**|**Description**|
| :- | :- | :- |
|FunctionParam|string|Parameters specific to actionName|
### **OMR API Example**
{{< gist "aspose-cloud" "b0e9305b5be4b21598cfdd5dd21102cb" "Examples-.NET-OMR-API-EXAMPLE.cs" >}}
### **OMR Response structure**
{{< gist "aspose-cloud" "b0e9305b5be4b21598cfdd5dd21102cb" "Examples-.NET-OMR-Response-Structure.cs" >}}

|**Field**|**Meaning**|**Values Examples**|
| :-: | :-: | :-: |
|int ErrorCode|Integer field that indicates whether any critical errors occured during task execution|<p>No errors: <0></p><p>Errors: <1|2|3..></p>|
|string ErrorText|String description of occured critical error. Empty if no critical errors occured|<p>No errors: <""></p><p>Errors: <"Error text example"></p>|
|Payload.Result|Structure that contains response result| |
|string TemplateId|<p>GUID string that is used to identify template on server</p><p>This value is assigned after Template Correction and used later in Template Finalization and Image Recognition</p>|<5b535525-72fe-453f-83e8-5a058569620e>|
|double ExecutionTime|Indicates how long it took to perform task on server.|<2.716449499130249>|
|ResponseFiles[]|<p>This structure holds array of files returned in response</p><p>Type and content of files differes depending on action</p>| |
|string Name|Name of the file|<"AnswerSheet.omr">, <"AnswerSheetScan.dat">|
|long Size|Size of the image in bytes|<546>|
|string Data|File data packed in base64 string|<"UXVlc3Rpb24xOkE....24xMDpDCg==">|
|Info|Structure that holds information about task execution| |
|string ResponseVersion|String value representing version of the response.|<"1.0">|
|int ProcessedTasksCount|Total amount of processed tasks|<1>, <17>|
|int SuccessfulTasksCount|Total amount of successful tasks, i.e. tasks that completed without errors|<1>, <15>|
|Details|<p>Structure that holds additional information regarding performed task.</p><p>It contents information like:</p><p>TaskResult, that indicates if each particular task passed or failed,</p><p>Task Messages, that contain warnings and other messages regarding task, etc.</p><p> </p><p>Content differ depeneding on action, see below for more details on each action.</p>| |


**Payload.Result.Files.Data** is a base64 string containing resulting file. Actual string data may be acquired in the following way:

**Base64 Data Unpacking**

```csharp

string correctedTemplate = Encoding.UTF8.GetString(Convert.FromBase64String(correctionResponse.Payload.Result.ResponseFiles[0].Data));

```

**Payload.Result.Files.Data** and **Payload.Result.Info.Details** content may vary depending on actionName. See examples for each action below.
## **Actions**
### **Generate Template**
Expected parameters values:

- **name:** <Path to a text file that contains template textual description>
- **actionName:**  <"GenerateTemplate">
- **functionParams:** <JSON string containing path to folder with images that are used in template textual description>

Invocation example:

{{< gist "aspose-cloud" "b0e9305b5be4b21598cfdd5dd21102cb" "Examples-.NET-Generate-Template.cs" >}}
#### ` `**Response content details**
- Within **OmrResponse.Payload.Result.Files** we produce generated .omr template file and .png image.
- Within **OmrResponse.Payload.Result.Info.Details** we produce JSON with following content:

##### **OmrResponse.Payload.Result.Info.Details** contains:

```csharp

string [] TaskMessages;
string TaskResult;

```


##### **OmrResponse.Payload.Result.Info.Details GenerateTemplate** example:

```json

{
  "Details": {
    "TaskMessages": [],
    "TaskResult": "Pass",
  }
}

```


##### **Full Response GenerateTemplate example:**

```json

{
  "ErrorCode": 0,
  "ErrorText": "",
  "Payload": {
    "Result": {
      "TemplateId": null,
      "ExecutionTime": 0.65801920890808,
      "ResponseFiles": [
        {
          "Name": "AnswerSheet.omr",
          "Size": 53155,
          "Data": "ewogICAgIl.....I6IFtdCn0="
        }, 
        {
          "Name": "AnswerSheet.png",
          "Size": 353437,
          "Data": ""iVBORw0KGg.....5ErkJggg==""
        }
      ],
      "Info": {
        "ResponseVersion": "1.0",
        "ProcessedTasksCount": 1,
        "SuccessfulTasksCount": 1,
        "Details": { 
	   "TaskMessages": [],
           "TaskResult":"Pass"
	}
      }
    }
  }
}

```
### **Correct Template**
Expected parameters values:

- **name:** <Path to an image file (image name) that is used to create template>
- **actionName:** <"CorrectTemplate">
- **functionParams:** <JSON string containing packed template data>

Invocation example:

{{< gist "aspose-cloud" "b0e9305b5be4b21598cfdd5dd21102cb" "Examples-.NET-Correct-Template.cs" >}}
#### **Response content details**
- Within **OmrResponse.Payload.Result.Files** we produce **.omrcr** file with corrected template JSON data
- Within **OmrResponse.Payload.Result.Info.Details** we produce JSON with following content:

##### **OmrResponse.Payload.Result.Info.Details** contains:

```csharp

string [] TaskMessages;

string TaskResult;

```

##### **OmrResponse.Payload.Result.Info.Details Correction** example:

```csharp

{

  "Details": {

    "TaskMessages": [

      "Initial image resolution was too low. We magnified image in 2.0 times"

    ],

    "TaskResult": "Pass"

  }

}

```

##### **Full Response Correction example**:

```json

{
  "ErrorCode": 0,
  "ErrorText": "",
  "Payload": {
	"Result": {
      "TemplateId": "5b535525-72fe-453f-83e8-5a058569620e",
      "ExecutionTime": 0.83317875862121582,
      "ResponseFiles": [
        {
          "Name": "AnswerSheet.omrcr",
          "Size": 27024,
          "Data": "ewogICAg.....GV0ZSI6IGZhbHNlCn0="
        }
      ],
      "Info": {
        "ResponseVersion": "1.0",
        "ProcessedTasksCount": 1,
        "SuccessfulTasksCount": 1,
        "Details": {
          "TaskMessages": [
            "Initial image resolution was too low. We magnified image in 2.0 times"
          ],
          "TaskResult": "Pass"
        }
      }
    }
  }
}

```
### **Finalize Template**
Expected parameters values:

- **name:** <omrcr file recieved after Template Correction>
- **actionName:** <"FinalizeTemplate">
- **functionParams:** <Template ID string, recieved after Template Correction>

Invocation example: 

{{< gist "aspose-cloud" "b0e9305b5be4b21598cfdd5dd21102cb" "Examples-.NET-Finalize-Template.cs" >}}
#### **Response content details**
- Within **OmrResponse.Payload.Result.Files** we produce RecognitionResult.dat file with finalization warnings and recognition data for the template image (note that it should not contain any results if image was filled)
- Within **OmrResponse.Payload.Result.Info.Details** we produce JSON with following content:

##### **OmrResponse.Payload.Result.Info.Details** contains:

```csharp

string [] TaskMessages;

string TaskResult;

```

##### **OmrResponse.Payload.Result.Info.Details Finalization** example:

```json

{
  "Details": {
    "TaskMessages": [],
    "TaskResult": "Pass"
  }
}

```

##### **Full Response Finalization example:**

```html

{
  "ErrorCode": 0,
  "ErrorText": "",
  "Payload": {
    "Result": {
      "TemplateId": "5b535525-72fe-453f-83e8-5a058569620e",
      "ExecutionTime": 5.373408794403076,
      "ResponseFiles": [
        {
          "Name": "RecognitionResult.dat",
          "Size": 182,
          "Data": "ewogICAg.....lc3VsdCI6IFtdCn0="
        }
      ],
      "Info": {
        "ResponseVersion": "1.0",
        "ProcessedTasksCount": 1,
        "SuccessfulTasksCount": 1,
        "Details": { 
		"TaskMessages": [],
            	"TaskResult":"Pass"
	}
      }
    }
  }
}

```
### **Recognize Image**
Expected parameters values:

- **name:** <Path to image file (image name) that should be recognized>
- **actionName:** <"RecognizeImage".>
- **functionParams:** <Template ID, recieved after Template Correction>

Invocation example:

{{< gist "aspose-cloud" "b0e9305b5be4b21598cfdd5dd21102cb" "Examples-.NET-Recognize-Image.cs" >}}
#### **Response content details**
- Within **OmrResponse.Payload.Result.Files** we produce .dat file with recognition data for the provided image.
- Within **OmrResponse.Payload.Result.Info.Details** we produce JSON with following content:

##### **OmrResponse.Payload.Result.Info.Details** contains:

```csharp

RecognitionStatistics[]
{
	string Name;
	string[] TaskMessages;
	string TaskResult;
	double RunSeconds;
}

```

##### **OmrResponse.Payload.Result.Info.Details Recognition** example:

```csharp
{
  "Details": {
    "RecognitionStatistics": [
      {
        "Name": "photo.jpg",
        "TaskMessages": [],
        "TaskResult": "Pass",
        "RunSeconds": 1.7953619956970215
      }
    ]
  }
}

```

##### **Full Response Recognition example:**

```html

{
  "ErrorCode": 0,
  "ErrorText": "",
  "Payload": {
    "Result": {
      "TemplateId": "5b535525-72fe-453f-83e8-5a058569620e",
      "ExecutionTime": 1.7034006118774414,
      "ResponseFiles": [
	{
          "Name": "photo.dat",
          "Size": 121,
          "Data": "UXVlc3R.....24xMDpDCg=="
        }
      ],
      "Info": {
        "ResponseVersion": "1.0",
        "ProcessedTasksCount": 1,
        "SuccessfulTasksCount": 1,
        "Details": {
    		"RecognitionStatistics": [
	    	  {
	        	"Name": "photo.jpg",
	    	    	"TaskMessages": [],
	        	"TaskResult": "Pass",
		        "RunSeconds": 1.3482120037078857
		      }
		    ]
		  }
      }
    }
  }
}

```
### **Grade Answers**
Expected parameters values:

- **name:** <Path to .dat file (file name) that contains recognition results that should be graded>
- **actionName:** <"GradeAnswers".>
- **functionParams:** <JSON string that contains grading rules>

Invocation example:

{{< gist "aspose-cloud" "b0e9305b5be4b21598cfdd5dd21102cb" "Examples-.NET-GradeAnswers.cs" >}}
#### **Response content details**
- Within **OmrResponse.Payload.Result.Files** we produce **.grade** file with grading results

Example of recognition results file:

##### **AsposeForm.dat**

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

### **PackedRules JSON example:**

#### **Rules JSON**

```java

{
  "Pages": [
    {
      "PageId": 12345,
      "CorrectPoints": 5,
      "IncorrectPoints": 2,
      "EmptyPoints": 1,
      "IncopleteAnswerPoints": 0.5,
      "IncopleteAnswersAllowed": true,
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

Grading results example (.grade file):

#### **AsposeForm.grade Example**

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
