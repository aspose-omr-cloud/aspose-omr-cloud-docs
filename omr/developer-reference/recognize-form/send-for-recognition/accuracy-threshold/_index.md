---
weight: 10
date: "2023-05-24"
author: "Vladimir Lapin"
type: docs
url: /recognition-accuracy-threshold/
feedback: OMRCLOUD
title: Fine tuning recognition accuracy
description: How to adjust the recognition accuracy to get reliable results under various conditions.
keywords:
- OMR
- recognition
- accuracy
- reliability
- threshold
- pen
- pencil
- marker
- send
- request
---

Different types of OMR forms can take different types of marks. Answer sheets usually require the bubbles to be completely filled in with a pen or marker. Ballot choices are typically marked with checkmarks or crosses. Surveys and applications are sometimes filled with a pencil so that corrections can be made.

In addition, paper quality, security watermarks, and lighting conditions when taking a photo of the filled form can adversely affect recognition accuracy.

All Aspose.OMR Cloud supports [`recognitionThreshold` parameter](/omr/send-form-for-recognition/#recognition-accuracy) that allows you to fine-tune form processing and produce results with near 100% accuracy. This parameter is called **recognition accuracy threshold**.

From a technical point of view, it defines the fill percentage of the bubble from `0` (empty bubble) to `100` (completely filled bubble). Lower values allow even the lightest marks (like dots or crosses) to be recognized, but may cause dirt, paper defects or watermarks to be treated as false positives. Higher values require a more solid fill and may cause pencil marks or small checks to be ignored.

![Recognition accuracy threshold](recognitionThreshold.png)

{{% alert color="primary" %}} 

It is very important that all the bubbles in the form are filled in the same manner by all respondents. Otherwise, the recognition results in batch processing may be unreliable, regardless of fine tuning.

{{% /alert %}} 

## Predefined recognition accuracy thresholds

**CheckBox** and **VerticalChoiceBox** [elements](/omr/design-form/) support setting the recognition accuracy in the form source code. This setting overrides the value of `recognitionThreshold` parameter for individual form elements. This can be very useful if you want a certain form element (like the consent field) to support lighter marks than the rest of the bubbles.

### Example

A form that requires all bubbles to be completely filled in with a pen, except for the consent box, which supports light checkmarks.

#### Form

```
#Are you considering evaluating other Aspose products?
	(Yes) Yes (No) No

?checkbox=I consent to the processing of the survey data:
	bubble_size=extrasmall
	font_size=10
	threshold=15
?content=Agree
	font_size=10
&checkbox
```

#### Recognition

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

#### Results

![Predefined recognition accuracy threshold for checkbox](predefined-accuracy-threshold.png)

## Usage tips

- Increase the recognition accuracy threshold if the paper you are printing forms on has security watermarks, such as ballots or answer sheets. Otherwise, watermarks within bubbles may be considered as choices.
- It is not recommended to set the recognition accuracy threshold to values higher than `70`. This would require almost the entire bubble to be completely filled with a dark pen, which can be a burden on respondents.
- The automatic recognition threshold (if the `recognitionThreshold` parameter is omitted) depends on the bubble type and provides reliable results in most use cases.
