---
weight: 50
date: "2023-05-24"
author: "Vladimir Lapin"
type: docs
url: /recognize-form/
title: Recognizing machine-readable forms
description: How to recognize the filled form with Aspose.OMR Cloud.
keywords:
- OMR
- recognition
- scan
- photo
- digitize
- result
---

To recognize a filled questionnaire, answer sheet, ballot, or other OMR form, digitize it in one of the [supported formats](/omr/supported-file-formats/). For best results, we recommend using a scanner (a basic office scanner or multifunction copier will suffice). If you do not have a scanner, you can simply take a picture of the form with any modern smartphone and upload the photo to your computer.

{{% alert color="primary" %}}
All [positioning markers](/omr/omr-form-structure/) must be present on the image.
{{% /alert %}}

Aspose.OMR Cloud recognizes a filled OMR form in 3 API calls:

1. [Get access token](/omr/authorization/).
2. [Send](/omr/send-form-for-recognition/) the form's image for recognition.
3. [Fetch](/omr/fetch-recognition-results/) recognition results.

Because Aspose.OMR Cloud is provided as a REST API, form recognition can be performed from any platform with Internet access.

Aspose also provides open-source [SDKs](/omr/recognize-form-sdk/) for all popular programming languages, that wrap all routine recognition operations into a few native methods. It makes interaction with Aspose.OMR Cloud services much easier, allowing you to focus on the task at hand rather than technical details.

{{% alert color="primary" %}}
Make sure the application has access to the **api.aspose.cloud** domain.
{{% /alert %}}
