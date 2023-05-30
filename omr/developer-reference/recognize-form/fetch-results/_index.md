---
weight: 20
date: "2023-05-24"
author: "Vladimir Lapin"
type: docs
url: /fetch-recognition-results/
feedback: OMRCLOUD
title: Fetch form recognition results
description: How to fetch from recognition results from Aspose.OMR Cloud.
keywords:
- OMR
- recognition
- accuracy
- reliability
- threshold
- pen
- pencil
- marker
- fetch
- download
---

When form is [submitted](/omr/send-form-for-recognition/) for recognition, it is [queued](/omr/how-it-works/) to ensure a stable response even under high load. To obtain the result, send a **GET** request to the `https://api.aspose.cloud/v5.0/omr/RecognizeTemplate/GetRecognizeTemplate` Aspose.OMR Cloud REST API endpoint. To authorize the request, pass the [access token](/omr/authorization/) in **Authorization** header (_Bearer authentication_).

Provide the [unique identifier](/omr/send-form-for-recognition/#return-value) of the recognition task in `id` parameter:

```bash
curl --location 'https://api.aspose.cloud/v5.0/omr/RecognizeTemplate/GetRecognizeTemplate?id=85bc0ca8-a76e-44f6-a7a3-e6263f7e24ee' \
--header 'Accept: text/plain' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...doQ6a6Nt2JlbO3fEGg'
```

## Recognition results

The recognition result is returned in JSON format in the response body.

```json
{
	"id": "85bc0ca8-a76e-44f6-a7a3-e6263f7e24ee",
	"responseStatusCode": "Ok",
	"results": [
		{
			"type": "Csv",
			"data": "RWxlbWVudCBOYW1lLFZhbHVlLApBbmltYWxzOTEsIiIKQW5pbWFsczky...gpQbGFudHM5MCwiIgo="
		}
	],
	"error": null
}
```

{{% alert color="primary" %}}
Generated form is stored in the Aspose cloud and can be obtained by the task ID within **24 hours** after the source code was sent for generation.
{{% /alert %}}

Property | Type | Description
--------- | ---- | -----------
`id` | string | Unique identifier of the generation task. Equals to the value of the `id` request property.
`responseStatusCode` | string | Generation response status.
`results` | array | Recognition results in the [requested](/omr/send-form-for-recognition/#output-format) output format as Base64 encoded string. You must decode them to save to a file, show or parse.
`error/messages` | array | Generation error messages, if any.<br />Even if the form is generated, you can still get notifications and warnings about non-fatal generation errors.
