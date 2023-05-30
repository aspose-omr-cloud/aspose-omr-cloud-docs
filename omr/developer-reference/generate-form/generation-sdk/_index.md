---
weight: 30
date: "2023-05-24"
author: "Vladimir Lapin"
type: docs
url: /generate-form-sdk/
feedback: OMRCLOUD
title: Generating machine-readable forms with Aspose.OMR Cloud SDK
description: How to render a printable OMR form and generate a recognition pattern file for Aspose.OMR engine.
keywords:
- render
- page
- form
- print
- paper
- pattern
- SDK
- code
- program
---

Although you can directly call the Aspose.OMR Cloud REST API to [send source code for generation](/omr/send-form-source-for-generation/) and [fetch printable form](/omr/fetch-printable-form/), there is a much easier way to implement OMR form generation functionality in your applications. We provide software development kits (SDKs) for all popular programming languages. They wrap up all routine operations such as establishing connections, sending API requests, and parsing responses into a few simple methods. It makes interaction with Aspose.OMR Cloud services much easier, allowing you to focus on business logic rather than technical details.

{{< tabs tabID="1" tabTotal="4" tabName1=".NET" >}}

{{< tab tabNum="1" >}}
```csharp
namespace Example
{
	using Aspose.Omr.Cloud.Sdk.Api;
	using Aspose.Omr.Cloud.Sdk.Model;

	internal class Program
	{
		static void Main(string[] args)
		{
			// Authorize your requests to Aspose.OMR Cloud API
			GenerateTemplateApi api = new GenerateTemplateApi();
			api.Configuration.ClientID = "<Client Id>";
			api.Configuration.ClientSecret = "<Client Secret>";
			// Read form's source code
			byte[] source = File.ReadAllBytes("source.txt");
			// Load images used on the form
			Dictionary<string, byte[]> images = new Dictionary<string, byte[]>();
			byte[] logoData = File.ReadAllBytes("logo.png");
			images.Add("logo.png", logoData);
			// Configure form design and layout
			PageSettings settings = new PageSettings {
				BubbleColor = Color.Indigo,
				PaperSize = PaperSize.Legal
			};
			// Generate printable form and recognition pattern
			OmrGenerateTask task = new OmrGenerateTask(source, settings, images);
			string taskID = api.PostGenerateTemplate(task);
			// Save printable form and recognition pattern
			OMRResponse result = api.GetGenerateTemplate(taskID);
			foreach(var item in result.Results)
			{
				string fileName = $"form.{item.Type}";
				File.WriteAllBytes(fileName, item.Data);
			}
		}
	}
}
```

Visit our GitHub repository for a working code and sample files: https://github.com/aspose-omr-cloud/aspose-omr-cloud-dotnet
{{< /tab >}}

{{< /tabs >}}
