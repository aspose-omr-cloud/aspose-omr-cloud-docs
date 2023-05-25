---
weight: 40
date: "2023-05-24"
author: "Vladimir Lapin"
type: docs
url: /generate-form/
title: Generating machine-readable forms
description: How to render a printable OMR form and generate a recognition pattern file for Aspose.OMR engine.
keywords:
- render
- page
- form
- print
- paper
- pattern
---

Aspose.OMR Cloud generates a printable OMR form in 3 API calls:

1. [Get access token](/omr/authorization/).
2. [Send](/omr/send-form-source-for-generation/) the form's [source code](/omr/design-form/) for rendering.
3. [Fetch](/omr/fetch-printable-form/) a printable form and a recognition pattern file.

Because Aspose.OMR Cloud is provided as a REST API, form generation can be performed from any platform with Internet access.

Aspose also provides open-source [SDKs](/omr/generate-form-sdk/) for all popular programming languages, that wrap all routine rendering operations into a few native methods. It makes interaction with Aspose.OMR Cloud services much easier, allowing you to focus on the task at hand rather than technical details.

{{% alert color="primary" %}}
Make sure the application has access to the **api.aspose.cloud** domain.
{{% /alert %}}
