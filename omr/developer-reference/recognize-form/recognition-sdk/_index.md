---
weight: 30
date: "2023-05-24"
author: "Vladimir Lapin"
type: docs
url: /recognize-form-sdk/
feedback: OMRCLOUD
title: Recognizing machine-readable forms with Aspose.OMR Cloud SDK
description: How to recognize a completed OMR form and generate a recognition pattern file for Aspose.OMR engine.
keywords:
- OMR
- recognition
- accuracy
- reliability
- threshold
- pen
- pencil
- marker
- SDK
- code
- program
---

Although you can directly call the Aspose.OMR Cloud REST API to [send a hand-filled form for recognition](/omr/send-form-for-recognition/) and [fetch recognition results](/omr/fetch-recognition-results/), there is a much easier way to implement OMR functionality in your applications. We provide software development kits (SDKs) for all popular programming languages. They wrap up all routine operations such as establishing connections, sending API requests, and parsing responses into a few simple methods. It makes interaction with Aspose.OMR Cloud services much easier, allowing you to focus on business logic rather than technical details.

{{< tabs tabID="1" tabTotal="4" tabName1=".NET" >}}

{{< tab tabNum="1" >}}
```csharp
namespace Example
{
	using Aspose.Omr.Cloud.Sdk.Api;
	using Aspose.Omr.Cloud.Sdk.Model;
	using System.IO;

	internal class Program
	{
		static void Main(string[] args)
		{
			// Authorize your requests to Aspose.OMR Cloud API
			RecognizeTemplateApi api = new RecognizeTemplateApi();
			api.Configuration.ClientID = "<Client Id>";
			api.Configuration.ClientSecret = "<Client Secret>";
			// Load the completed form
			byte[] form = File.ReadAllBytes("john-doe.jpg");
			// Load recognition pattern
			byte[] pattern = File.ReadAllBytes("form.omr");
			// Send form for recognition with 35% accuracy threshold
			OmrRecognizeTask task = new OmrRecognizeTask(new List<byte[]> { form }, pattern, 35, S3DataType.Csv);
			string taskId = api.PostRecognizeTemplate(task);
			// Save recognition results to a file
			OMRRecognitionResponse result = api.GetRecognizeTemplate(taskId);
			File.WriteAllBytes("result.csv", result.Results[0].Data);
		}
	}
}
```

Visit our GitHub repository for a working code and sample files: https://github.com/aspose-omr-cloud/aspose-omr-cloud-dotnet
{{< /tab >}}

{{< /tabs >}}
