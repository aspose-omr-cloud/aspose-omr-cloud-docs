---
weight: 10
date: "2023-05-24"
author: "Vladimir Lapin"
type: docs
url: /send-form-source-for-generation/
title: Send OMR form source code for generation
description: How to send the OMR form source code to Aspose.OMR cloud for rendering.
keywords:
- render
- page
- form
- print
- paper
- pattern
- send
- request
---

To generate a printable OMR form from a [source code](/omr/design-form/), send a **POST** request to the `https://api.aspose.cloud/v5.0/omr/GenerateTemplate/PostGenerateTemplate` Aspose.OMR Cloud REST API endpoint. To authorize the request, pass the [access token](/omr/authorization/) in **Authorization** header (_Bearer authentication_).

The source code and rendering parameters are provided in JSON format in the request body.

```json
{
  "MarkupFile": "Source code as Base64 string",
  "Images": {
  	"image1.png": "Base64 encoded image file",
  	"image2.png": "Base64 encoded image file"
  },
  "settings": {
  	"FontFamily": "Arial",
  	"FontStyle": "Regular",
  	"FontSize": 15,
  	"PaperSize": "A4",
  	"BubbleColor": "Red",
  	"PageMarginLeft": 50,
  	"Orientation": "Vertical",
  	"BubbleSize": "Normal"
  }
}
```

## Providing source code

The form's [source code](/omr/design-form/) is provided in a value of `MarkupFile` property as a Base64 encoded string.

## Providing images

If the OMR form contains images, they must be provided as `Images` property entries, where the image filename referenced in the source code is the key and the Base64-encoded content of the image file is the value.

{{< tabs tabID="1" tabTotal="2" tabName1="Source code" tabName2="Images" >}}
{{< tab tabNum="1" >}}
```text
?image=logo.png
	align=center
?empty_line=
?text=Aspose.OMR Cloud
	align=center
	font_size=24
?image=photo.png
```
{{< /tab >}}
{{< tab tabNum="2" >}}
```json
"Images": {
	"logo.png": "P3BhZ2U9Cj90ZXh0PUJpb2xvZ3kgUXVpejogUGxhbnRzCglmb...vdW50PTUKJnBhZ2U=",
	"photo.png": "P3BhZ2U9gUXVpejogUGxhbnRzCglmbpejogUGxhbnRzCglmb...vdW50PTUKJnBhZaU="
},
```
{{< /tab >}}
{{< /tabs >}}

{{% alert color="caution" %}}
Base64 encoded image can be very long, especially when using scans and high resolution photos. As a result, you may encounter an error when calling form generation via cURL in a shell command. Use the `getconf ARG_MAX` command to check the maximum length of the command arguments (in bytes).
{{% /alert %}}

## Rendering parameters

The paper size, orientation, font, and other global layout settings are configured through `Settings` property.

Setting | Type | Values | Description
------- | ---- | ------ | -----------
`PaperSize` | string | <ul><li>`A4` (210 x 297 mm, 2480 x 3508 pixels)</li><li>`Letter` (215.9 x 279.4 mm, 2551 x 3295 pixels)</li><li>`Legal` (215.9 x 355.6 mm, 2551 x 4205 pixels)</li></ul> | Physical page size.
`Orientation` | string | <ul><li>`Horizontal` (landscape)</li><li>`Vertical` (portrait)</li></ul> | Page orientation.
`PageMarginLeft` | number | Number of pixels. | The width of the left page margin in pixels.
`FontFamily` | string | Font name. Check the list of [supported fonts](/omr/supported-fonts/). | Font family for all texts, except for those directly overridden in the source code. For example, `Courier New`.<br />You can only use fonts that are supported in the cloud!
`FontSize` | number | Font size in pixels. | Font size for all texts, except for those directly overridden in the source code.
`FontStyle` | string | <ul><li>`Regular`</li><li>`Bold`</li><li>`Italic`</li><li>`Underline`</li><li>`Strikeout`</li></ul> | Font style for all texts, except for those directly overridden in the source code.
`BubbleColor` | string | One of the [supported color codes](/omr/supported-colors/). | Color of all answer bubbles in the form.
`BubbleSize` | string | <ul><li>`Extrasmall` (40 pixels)</li><li>`Small` (50 pixels)</li><li>`Normal` (60 pixels)</li><li>`Large` (80 pixels)</li><li>`Extralarge` (100 pixels)</li></ul> | Size of answer bubbles, except for those directly overridden in the source code.

## Return value

If successful, this method returns a string with a unique identifier (GUID) of the form generation request in the [queue](/omr/how-it-works/).

Otherwise, it returns a HTTP status code corresponding to the error.

## What's next

Form generation will take a few seconds, depending on the complexity of the form, number of images, and the current Aspose.Cloud load. See the article [Fetch printable form](/omr/fetch-printable-form/) for information on how to get a machine-readable form image and a recognition pattern from the server.

## cURL example

{{< tabs tabID="2" tabTotal="2" tabName1="Request" tabName2="Response" >}}
{{< tab tabNum="1" >}}
```bash
curl --location --request POST 'https://api.aspose.cloud/v5.0/omr/GenerateTemplate/PostGenerateTemplate' \
--header 'Accept: text/plain' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsI...TMpXEfk3BOozpOiEhetRKfDNc8LEPQHBqg' \
--data '{
	"MarkupFile": "P3BhZ2U9Cj90ZXh0PUJpb2xvZ3kgUXVpejogUGxhbnRzCglmb...vdW50PTUKJnBhZ2U=",
	"Images": {},
	"Settings": {
		"PaperSize": "A4",
		"BubbleColor": "red"
	}
}'
```
{{< /tab >}}
{{< tab tabNum="2" >}}
```
7ec63522-e35f-4f9d-8b06-0da1876220b6
```
{{< /tab >}}
{{< /tabs >}}
