---
weight: 10
date: "2023-05-24"
author: "Vladimir Lapin"
type: docs
url: /send-form-for-recognition/
feedback: OMRCLOUD
title: Send OMR form for recognition
description: How to send the filled OMR form to Aspose.OMR cloud for recognition.
keywords:
- OMR
- recognition
- scan
- photo
- digitize
- result
- send
- request
---

To recognize a filled OMR form, send a **POST** request to the `https://api.aspose.cloud/v5.0/omr/RecognizeTemplate/PostRecognizeTemplate` Aspose.OMR Cloud REST API endpoint. To authorize the request, pass the [access token](/omr/authorization/) in **Authorization** header (_Bearer authentication_).

The source code and rendering parameters are provided in JSON format in the request body.

```json
{
  "Images": [
  	"Base64 encoded form image"
  ],
  "omrFile": "Base64 encoded recognition pattern",
  "outputFormat": "CSV",
  "recognitionThreshold": 35
}
```

## Providing the form

The form's [image](/omr/design-form/) is provided in a value of `Images` array as a Base64 encoded string. At the moment, only one image will be recognized; other images are ignored.

In addition to the image, you must provide the [recognition pattern](/omr/fetch-printable-form/#recognition-results) generated along with the printable form. The recognition pattern is specified as a Base64 encoded string in a value of `omrFile` parameter. 

{{% alert color="info" %}}
**Recovering a recognition pattern file**

If you have lost the recognition pattern file for the questionnaire, simply [generate](/omr/generate-form/) it again from the form source code using exactly the same paper size, orientation, font, and other layout setting.
{{% /alert %}}

## Output format

Aspose.OMR Cloud can return recognition results in the most popular data storage formats. Recognition result format is specified in the value of `outputFormat` property.

Format | Value | Description
------ | ----- | -----------
Comma-separated values (CSV) | `CSV` | A lightweight text format that uses a comma to separate values in a table-like structure. Best suited for spreadsheet applications and simple relational database tables.
JSON | `JSON` | The most popular popular open standard format for describing nested data structures. Best suited for NoSQL databases or web.
Etensible Markup Language (XML) | `XML` | A universal format for most systems - from databases to CRM.

## Recognition accuracy

Recognition accuracy threshold is specified in the value of `recognitionThreshold` parameter.

Read [Fine tuning recognition accuracy](/omr/recognition-accuracy-threshold/) for details.

## Return value

If successful, this method returns a string with a unique identifier (GUID) of the form recognition request in the [queue](/omr/how-it-works/).

Otherwise, it returns a HTTP status code corresponding to the error.

## What's next

Form recognition will take a few seconds, depending on the complexity of the form, image size, and the current Aspose.Cloud load. See the article [Fetch form recognition results](/omr/fetch-recognition-results/) for information on how to get recognition results from the server.

## cURL example

{{< tabs tabID="2" tabTotal="2" tabName1="Request" tabName2="Response" >}}
{{< tab tabNum="1" >}}
```bash
curl --location 'https://api.aspose.cloud/v5.0/omr/RecognizeTemplate/PostRecognizeTemplate' \
--header 'Accept: text/plain' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...doQ6a6Nt2JlbO3fEGg' \
--data '{
	"Images": [
		"iVBORw0KGgoAAAANSUhEUgAACbAAAA2...rR2lwI/PWEAAAAAElFTkSuQmCC"
	],
	"omrFile": "ewoJIlZlcnNpb24iOiAiMS4wIiwKCSJOYW1lIjogIk15V...CSJJc0dlbmVyYXRlZCI6IHRydWUKfQ==",
	"outputFormat": "CSV",
	"recognitionThreshold": 35
}'
```
{{< /tab >}}
{{< tab tabNum="2" >}}
```
85bc0ca8-a76e-44f6-a7a3-e6263f7e24ee
```
{{< /tab >}}
{{< /tabs >}}
