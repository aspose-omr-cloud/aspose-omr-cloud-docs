---
weight: 20
date: "2023-05-24"
author: "Vladimir Lapin"
type: docs
url: /fetch-printable-form/
feedback: OMRCLOUD
title: Fetch printable form
description: How to fetch a generated printable OMR form and a recognition pattern file from Aspose.OMR Cloud.
keywords:
- render
- page
- form
- print
- paper
- pattern
- get
- fetch
- download
---

When form's source code is [submitted](/omr/send-form-source-for-generation/) for generation, it is [queued](/omr/how-it-works/) to ensure a stable response even under high load. To obtain the result, send a **GET** request to the `https://api.aspose.cloud/v5.0/omr/GenerateTemplate/GetGenerateTemplate` Aspose.OMR Cloud REST API endpoint. To authorize the request, pass the [access token](/omr/authorization/) in **Authorization** header (_Bearer authentication_).

Provide the [unique identifier](/omr/send-form-source-for-generation/#return-value) of the generation task in `id` parameter:

```bash
curl --location 'https://api.aspose.cloud/v5.0/omr/GenerateTemplate/GetGenerateTemplate?id=7ec63522-e35f-4f9d-8b06-0da1876220b6' \
--header 'Accept: text/plain' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...TMpXEfk3BOozpOiEhetRKfDNc8LEPQHBqg'
```

## Generated form

The form is returned in JSON format in the response body.

```json
{
	"id": "7ec63522-e35f-4f9d-8b06-0da1876220b6",
	"responseStatusCode": "Ok",
	"results": [
		{
			"type": "Png",
			"data": "iVBORw0KGgoAAAANSUhEUgAACbAAAA20CAYAAAAuvPkNAAAACXBIWXMAAA7DAAAOwwHHb6hkAAB...N7rR2lwI/PWEAAAAAElFTkSuQmCC"
		},
		{
			"type": "Omr",
			"data": "ewoJIlZlcnNpb24iOiAiMS4wIiwKCSJOYW1lIjogIk15VGVtcGxhdGUiLAoJIlBhZ2VzIjogWwo...VyYXRlZCI6IHRydWUKfQ=="
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
`results` | array | This list includes at least 2 entries:<br /><ul><li>**Printable form pages** as PNG images (`"type": "Png"`). Their dimensions match the [provided](/omr/send-form-source-for-generation/#rendering-parameters) paper size and orientation. Each page is always saved as a separate file.</li><li>A **recognition pattern** used by Aspose.OMR recognition engine, in a special .OMR format (`"type": "Omr"`). This file is required for recognizing filled forms, make sure you save it along with the printable form images!</li></ul>
`error/messages` | array | Generation error messages, if any.<br />Even if the form is generated, you can still get notifications and warnings about non-fatal generation errors.

{{% alert color="primary" %}}
Printable form pages and a recognition pattern are returned as Base64 encoded strings. You must decode them to save to a file.
{{% /alert %}}
