---
title: "OMR API Specification"
type: docs
url: /omr-api-specification/
weight: 20
---

## **Function Specifications**

At present, Aspose.OMR for Cloud API exposes single function with string parameter that determines which specific action should be performed.

|**API**|**Type**|**Description**|**Swagger Link**|
| :- | :- | :- | :- |
|/omr​/{name}​/runOmrTask|POST|Run specific OMR task|[PostRunOmrTask](https://apireference.aspose.cloud/omr/#/Omr/PostRunOmrTask)|

### **OMRFunctionParam Description**
**OMRFunctionParam** is a separate class that has **FunctionParam** property. This property accepts string parameters, usually JSON strings, that are specific to each action. See examples given below for each action.

### **cURL Example**

{{< tabs tabTotal="2" tabID="1" tabName1="Request" tabName2="Response" >}}

{{< tab tabNum="1" >}}

```java

// First get Access Token
// Get App Key and App SID from https://dashboard.aspose.cloud/

curl -v "https://api.aspose.cloud/connect/token" -X POST -d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" -H "Content-Type: application/x-www-form-urlencoded" -H "Accept: application/json"

```
```java

curl -X POST "https://api.aspose.cloud/v3.0/omr/Aspose_test.txt/runOmrTask?actionName=GenerateTemplate" -H "accept: application/json" -H "authorization: Bearer <jwt token>" -H "Content-Type: application/json" -H "x-aspose-client: Containerize.Swagger" -d "{\"FunctionParam\": null, \"AdditionalParam\": null}"

```

{{< /tab >}}

{{< tab tabNum="2" >}}

```java

{
  "ErrorCode": 0,
  "ErrorText": "string",
  "Payload": {
    "Result": {
      "TemplateId": "string",
      "ExecutionTime": 0,
      "ResponseFiles": [
        {
          "Name": "string",
          "Size": 0,
          "Data": "string"
        }
      ],
      "Info": {
        "ResponseVersion": "string",
        "ProcessedTasksCount": 0,
        "SuccessfulTasksCount": 0,
        "Details": {
          "TaskMessages": [
            "string"
          ],
          "TaskResult": "string",
          "RecognitionStatistics": [
            {
              "Name": "string",
              "TaskMessages": [
                "string"
              ],
              "TaskResult": "string",
              "RunSeconds": 0
            }
          ]
        }
      }
    }
  },
  "ServerStat": {
    "StorageDownloadTime": "string",
    "OmrFunctionCallTime": "string"
  }
}

```

{{< /tab >}}

{{< /tabs >}}


## **SDKs**
Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of making requests and handling responses and lets you focus on writing code specific to your particular project. Checkout our [GitHub repository](https://github.com/aspose-omr-cloud) for a complete list of Aspose.OMR SDKs along with working examples, to get you started in no time.
### **SDK Examples**

#### **Actions**
##### **Generate Template**
Expected parameters values:

- **name:** <Path to a text file that contains template textual description>
- **actionName:**  <"GenerateTemplate">
- **functionParams:** <JSON string containing path to folder with images that are used in template textual description>

##### **cURL Example for Generate Template**

{{< tabs tabTotal="2" tabID="2" tabName1="Request" tabName2="Response" >}}

{{< tab tabNum="1" >}}

```java

curl -X POST "https://api.aspose.cloud/v3.0/omr/Aspose_test.txt/runOmrTask?actionName=GenerateTemplate" -H "accept: application/json" -H "authorization: Bearer <jwt token>" -H "Content-Type: application/json" -H "x-aspose-client: Containerize.Swagger" -d "{\"FunctionParam\": null, \"AdditionalParam\": null}"

```

{{< /tab >}}

{{< tab tabNum="2" >}}

```java

{
  "ErrorCode": 0,
  "ErrorText": "string",
  "Payload": {
    "Result": {
      "TemplateId": "string",
      "ExecutionTime": 0,
      "ResponseFiles": [
        {
          "Name": "string",
          "Size": 0,
          "Data": "string"
        }
      ],
      "Info": {
        "ResponseVersion": "string",
        "ProcessedTasksCount": 0,
        "SuccessfulTasksCount": 0,
        "Details": {
          "TaskMessages": [
            "string"
          ],
          "TaskResult": "string",
          "RecognitionStatistics": [
            {
              "Name": "string",
              "TaskMessages": [
                "string"
              ],
              "TaskResult": "string",
              "RunSeconds": 0
            }
          ]
        }
      }
    }
  },
  "ServerStat": {
    "StorageDownloadTime": "string",
    "OmrFunctionCallTime": "string"
  }
}

```

{{< /tab >}}

{{< /tabs >}}

###### **Example**:

{{< tabs tabTotal="7" tabID="4" tabName1="C#" tabName2="Java & Android" tabName3="Node.js" tabName4="PHP" tabName5="Python" tabName6="Perl" tabName7="Ruby">}}

{{< tab tabNum="1" >}}

{{< gist "aspose-cloud" "904f29c358f2a767f93cff6bfef680eb" "Example-GenerateTemplate.cs" >}}

{{< /tab >}}

{{< tab tabNum="2" >}}

{{< gist "aspose-cloud" "cd72000173883c3469015d0f0efcd6f9" "Example-GenerateTemplate.java" >}}

{{< /tab >}}

{{< tab tabNum="3" >}}

{{< gist "aspose-cloud" "9f031c49ff23d1a41298ad665944aefe" "Example-GenerateTemplate.ts" >}}

{{< /tab >}}

{{< tab tabNum="4" >}}

{{< gist "aspose-cloud" "3beac24bdea025c4aad5a2f1ea81be9f" "Example-GenerateTemplate.php" >}}

{{< /tab >}}

{{< tab tabNum="5" >}}

{{< gist "aspose-cloud" "d226c533f812b92ae5218383e05c4d02" "Example-GenerateTemplate.py" >}}

{{< /tab >}}

{{< tab tabNum="6" >}}

{{< gist "aspose-cloud" "3ad721f30f4b85a9a4bab99ec5696cb3" "Example-GenerateTemplate.pl" >}}

{{< /tab >}}

{{< tab tabNum="7" >}}

{{< gist "aspose-cloud" "5b7fccaec056fa66b55b2d7ad22b9c20" "Example-GenerateTemplate.rb" >}}

{{< /tab >}}

{{< /tabs >}}

###### **Response content details**
- Within **OmrResponse.Payload.Result.Files** we produce generated .omr template file and .png image.
- Within **OmrResponse.Payload.Result.Info.Details** we produce JSON with following content:

**OmrResponse.Payload.Result.Info.Details** contains:

```csharp

string [] TaskMessages;
string TaskResult;

```


**OmrResponse.Payload.Result.Info.Details GenerateTemplate** example:

```json

{
  "Details": {
    "TaskMessages": [],
    "TaskResult": "Pass",
  }
}

```


**Full Response GenerateTemplate example:**

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
##### **Correct Template**
Expected parameters values:

- **name:** <Path to an image file (image name) that is used to create template>
- **actionName:** <"CorrectTemplate">
- **functionParams:** <JSON string containing packed template data>

##### **cURL Example for Correct Template**

{{< tabs tabTotal="2" tabID="3" tabName1="Request" tabName2="Response" >}}

{{< tab tabNum="1" >}}

```java

curl -X POST "https://api.aspose.cloud/v3.0/omr/Aspose_test.png/runOmrTask?actionName=CorrectTemplate" -H "accept: application/json" -H "authorization: Bearer <jwt token>" -H "Content-Type: application/json" -H "x-aspose-client: Containerize.Swagger" -d "{\"FunctionParam\": \"{\\r\ \\\"Files\":[\r\n{\r\n\"Name\":\"Aspose_test.omr\",\r\n\"Size\": xxxx,\r\n\"Data\": \"xxxx\"\r\n}\r\n]\r\n}", \"AdditionalParam\": null}"

```

{{< /tab >}}

{{< tab tabNum="2" >}}

```java

{
  "ErrorCode": 0,
  "ErrorText": "string",
  "Payload": {
    "Result": {
      "TemplateId": "string",
      "ExecutionTime": 0,
      "ResponseFiles": [
        {
          "Name": "string",
          "Size": 0,
          "Data": "string"
        }
      ],
      "Info": {
        "ResponseVersion": "string",
        "ProcessedTasksCount": 0,
        "SuccessfulTasksCount": 0,
        "Details": {
          "TaskMessages": [
            "string"
          ],
          "TaskResult": "string",
          "RecognitionStatistics": [
            {
              "Name": "string",
              "TaskMessages": [
                "string"
              ],
              "TaskResult": "string",
              "RunSeconds": 0
            }
          ]
        }
      }
    }
  },
  "ServerStat": {
    "StorageDownloadTime": "string",
    "OmrFunctionCallTime": "string"
  }
}

```

{{< /tab >}}

{{< /tabs >}}

###### **Example**:

{{< tabs tabTotal="7" tabID="4" tabName1="C#" tabName2="Java & Android" tabName3="Node.js" tabName4="PHP" tabName5="Python" tabName6="Perl" tabName7="Ruby">}}

{{< tab tabNum="1" >}}

{{< gist "aspose-cloud" "904f29c358f2a767f93cff6bfef680eb" "Example-CorrectTemplate.cs" >}}

{{< /tab >}}

{{< tab tabNum="2" >}}

{{< gist "aspose-cloud" "cd72000173883c3469015d0f0efcd6f9" "Example-CorrectTemplate.java" >}}

{{< /tab >}}

{{< tab tabNum="3" >}}

{{< gist "aspose-cloud" "9f031c49ff23d1a41298ad665944aefe" "Example-CorrectTemplate.ts" >}}

{{< /tab >}}

{{< tab tabNum="4" >}}

{{< gist "aspose-cloud" "3beac24bdea025c4aad5a2f1ea81be9f" "Example-CorrectTemplate.php" >}}

{{< /tab >}}

{{< tab tabNum="5" >}}

{{< gist "aspose-cloud" "d226c533f812b92ae5218383e05c4d02" "Example-CorrectTemplate.py" >}}

{{< /tab >}}

{{< tab tabNum="6" >}}

{{< gist "aspose-cloud" "3ad721f30f4b85a9a4bab99ec5696cb3" "Example-CorrectTemplate.pl" >}}

{{< /tab >}}

{{< tab tabNum="7" >}}

{{< gist "aspose-cloud" "5b7fccaec056fa66b55b2d7ad22b9c20" "Example-CorrectTemplate.rb" >}}

{{< /tab >}}

{{< /tabs >}}

###### **Response content details**
- Within **OmrResponse.Payload.Result.Files** we produce **.omrcr** file with corrected template JSON data
- Within **OmrResponse.Payload.Result.Info.Details** we produce JSON with following content:

**OmrResponse.Payload.Result.Info.Details** contains:

```csharp

string [] TaskMessages;
string TaskResult;

```

**OmrResponse.Payload.Result.Info.Details Correction** example:

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

**Full Response Correction example**:

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
##### **Finalize Template**
Expected parameters values:

- **name:** <omrcr file recieved after Template Correction>
- **actionName:** <"FinalizeTemplate">
- **functionParams:** <Template ID string, recieved after Template Correction>

##### **cURL Example for Finalize Template**

{{< tabs tabTotal="2" tabID="6" tabName1="Request" tabName2="Response" >}}

{{< tab tabNum="1" >}}

```java

curl -X POST "https://api.aspose.cloud/v3.0/omr/Aspose_test.omrcr/runOmrTask?actionName=FinalizeTemplate" -H "accept: application/json" -H "authorization: Bearer <jwt token>" -H "Content-Type: application/json" -H "x-aspose-client: Containerize.Swagger" -d "{ \"FunctionParam\": \"xxxx\", \"AdditionalParam\": null}"

```

{{< /tab >}}

{{< tab tabNum="2" >}}

```java

{
  "ErrorCode": 0,
  "ErrorText": "string",
  "Payload": {
    "Result": {
      "TemplateId": "string",
      "ExecutionTime": 0,
      "ResponseFiles": [
        {
          "Name": "string",
          "Size": 0,
          "Data": "string"
        }
      ],
      "Info": {
        "ResponseVersion": "string",
        "ProcessedTasksCount": 0,
        "SuccessfulTasksCount": 0,
        "Details": {
          "TaskMessages": [
            "string"
          ],
          "TaskResult": "string",
          "RecognitionStatistics": [
            {
              "Name": "string",
              "TaskMessages": [
                "string"
              ],
              "TaskResult": "string",
              "RunSeconds": 0
            }
          ]
        }
      }
    }
  },
  "ServerStat": {
    "StorageDownloadTime": "string",
    "OmrFunctionCallTime": "string"
  }
}

```

{{< /tab >}}

{{< /tabs >}}

###### **Example**:

{{< tabs tabTotal="7" tabID="4" tabName1="C#" tabName2="Java & Android" tabName3="Node.js" tabName4="PHP" tabName5="Python" tabName6="Perl" tabName7="Ruby">}}

{{< tab tabNum="1" >}}

{{< gist "aspose-cloud" "904f29c358f2a767f93cff6bfef680eb" "Example-FinalizeTemplate.cs" >}}

{{< /tab >}}

{{< tab tabNum="2" >}}

{{< gist "aspose-cloud" "cd72000173883c3469015d0f0efcd6f9" "Example-FinalizeTemplate.java" >}}

{{< /tab >}}

{{< tab tabNum="3" >}}

{{< gist "aspose-cloud" "9f031c49ff23d1a41298ad665944aefe" "Example-FinalizeTemplate.ts" >}}

{{< /tab >}}

{{< tab tabNum="4" >}}

{{< gist "aspose-cloud" "3beac24bdea025c4aad5a2f1ea81be9f" "Example-FinalizeTemplate.php" >}}

{{< /tab >}}

{{< tab tabNum="5" >}}

{{< gist "aspose-cloud" "d226c533f812b92ae5218383e05c4d02" "Example-FinalizeTemplate.py" >}}

{{< /tab >}}

{{< tab tabNum="6" >}}

{{< gist "aspose-cloud" "3ad721f30f4b85a9a4bab99ec5696cb3" "Example-FinalizeTemplate.pl" >}}

{{< /tab >}}

{{< tab tabNum="7" >}}

{{< gist "aspose-cloud" "5b7fccaec056fa66b55b2d7ad22b9c20" "Example-FinalizeTemplate.rb" >}}

{{< /tab >}}

{{< /tabs >}}

###### **Response content details**
- Within **OmrResponse.Payload.Result.Files** we produce RecognitionResult.dat file with finalization warnings and recognition data for the template image (note that it should not contain any results if image was filled)
- Within **OmrResponse.Payload.Result.Info.Details** we produce JSON with following content:

 **OmrResponse.Payload.Result.Info.Details** contains:

```csharp

string [] TaskMessages;

string TaskResult;

```

**OmrResponse.Payload.Result.Info.Details Finalization** example:

```json

{
  "Details": {
    "TaskMessages": [],
    "TaskResult": "Pass"
  }
}

```

**Full Response Finalization example:**

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
##### **Recognize Image**
Expected parameters values:

- **name:** <Path to image file (image name) that should be recognized>
- **actionName:** <"RecognizeImage".>
- **functionParams:** <Template ID, recieved after Template Correction>

##### **cURL Example for Recognize Template**

{{< tabs tabTotal="2" tabID="5" tabName1="Request" tabName2="Response" >}}

{{< tab tabNum="1" >}}

```java

curl -X POST "https://api.aspose.cloud/v3.0/omr/Aspose_test.omrcr/runOmrTask?actionName=RecognizeImage" -H "accept: application/json" -H "authorization: Bearer <jwt token>" -H "Content-Type: application/json" -H "x-aspose-client: Containerize.Swagger" -d "{ \"FunctionParam\": \"xxxx\", \"AdditionalParam\": null}"

```

{{< /tab >}}

{{< tab tabNum="2" >}}

```java

{
  "ErrorCode": 0,
  "ErrorText": "string",
  "Payload": {
    "Result": {
      "TemplateId": "string",
      "ExecutionTime": 0,
      "ResponseFiles": [
        {
          "Name": "string",
          "Size": 0,
          "Data": "string"
        }
      ],
      "Info": {
        "ResponseVersion": "string",
        "ProcessedTasksCount": 0,
        "SuccessfulTasksCount": 0,
        "Details": {
          "TaskMessages": [
            "string"
          ],
          "TaskResult": "string",
          "RecognitionStatistics": [
            {
              "Name": "string",
              "TaskMessages": [
                "string"
              ],
              "TaskResult": "string",
              "RunSeconds": 0
            }
          ]
        }
      }
    }
  },
  "ServerStat": {
    "StorageDownloadTime": "string",
    "OmrFunctionCallTime": "string"
  }
}

```

{{< /tab >}}

{{< /tabs >}}

###### **Example**:

{{< tabs tabTotal="7" tabID="4" tabName1="C#" tabName2="Java & Android" tabName3="Node.js" tabName4="PHP" tabName5="Python" tabName6="Perl" tabName7="Ruby">}}

{{< tab tabNum="1" >}}

{{< gist "aspose-cloud" "904f29c358f2a767f93cff6bfef680eb" "Example-RecognizeImage.cs" >}}

{{< /tab >}}

{{< tab tabNum="2" >}}

{{< gist "aspose-cloud" "cd72000173883c3469015d0f0efcd6f9" "Example-RecognizeImage.java" >}}

{{< /tab >}}

{{< tab tabNum="3" >}}

{{< gist "aspose-cloud" "9f031c49ff23d1a41298ad665944aefe" "Example-RecognizeImage.ts" >}}

{{< /tab >}}

{{< tab tabNum="4" >}}

{{< gist "aspose-cloud" "3beac24bdea025c4aad5a2f1ea81be9f" "Example-RecognizeImage.php" >}}

{{< /tab >}}

{{< tab tabNum="5" >}}

{{< gist "aspose-cloud" "d226c533f812b92ae5218383e05c4d02" "Example-RecognizeImage.py" >}}

{{< /tab >}}

{{< tab tabNum="6" >}}

{{< gist "aspose-cloud" "3ad721f30f4b85a9a4bab99ec5696cb3" "Example-RecognizeImage.pl" >}}

{{< /tab >}}

{{< tab tabNum="7" >}}

{{< gist "aspose-cloud" "5b7fccaec056fa66b55b2d7ad22b9c20" "Example-RecognizeImage.rb" >}}

{{< /tab >}}

{{< /tabs >}}

###### **Response content details**
- Within **OmrResponse.Payload.Result.Files** we produce .dat file with recognition data for the provided image.
- Within **OmrResponse.Payload.Result.Info.Details** we produce JSON with following content:

**OmrResponse.Payload.Result.Info.Details** contains:

```csharp

RecognitionStatistics[]
{
	string Name;
	string[] TaskMessages;
	string TaskResult;
	double RunSeconds;
}

```

**OmrResponse.Payload.Result.Info.Details Recognition** example:

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

**Full Response Recognition example:**

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