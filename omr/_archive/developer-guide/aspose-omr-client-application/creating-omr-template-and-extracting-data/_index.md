---
title: "Creating OMR Template and Extracting Data"
type: docs
url: /creating-omr-template-and-extracting-data/
weight: 10
---

{{% alert color="primary" %}} 

[Aspose.OMR.Client](https://github.com/aspose-omr-cloud/aspose-omr-cloud-dotnet/tree/master/Aspose.OMR.Client) is a WPF application (.NET version 4.6.2) that allows developers to create OMR templates, correct/update existing OMR templates and perform OMR recognition using Aspose.OMR.Cloud engine.

{{% /alert %}} 

Aspose.OMR.Client tool allows developers to:

- Create template markup and save it (.omr file)
- Perform template correction and finalization
- Recognize filled OMR sheets using templates and export the results (.csv).

You can easily understand the process to create/update an OMR template with the help of following flowchart:

![todo:image_alt_text](creating-omr-template-and-extracting-data_1.png)
## **Working with Aspose.OMR.Client**
Before getting started with [Aspose.OMR.Client tool](https://github.com/aspose-omr-cloud/aspose-omr-cloud-dotnet/tree/master/Aspose.OMR.Client), please visit [OMR Template Requirements](/omr/omr-template-requirements/), which describes the requirements and recommendations for creating templates. At present, supported image formats include:

- PNG
- JPG
- TIFF
- GIF
### **Provide Credentials**
- The usage of OMR API is required to be registered at <https://dashboard.aspose.cloud/>. Please, recieve APP KEY and APP SID at our web-site. You should enter them within OMR.Client before calling OMR API
- On the first application launch the credentials dialog should appear asking you to provide APP KEY and APP SID values

![todo:image_alt_text](creating-omr-template-and-extracting-data_2.png)

- This dialog can also be accessed via **Settings->Credentials** button on toolbar
- While working with Aspose.OMR.Client application, you can visit your [cloud dashboard](https://dashboard.aspose.cloud/#/files) to manage files that were uploaded using client application
### **Create new Template**
User can choose whether to create a new template or to work with existing one. Here we will focus on the creation of new template. Whereas work with loaded template does not differ from previous scenario.

![todo:image_alt_text](creating-omr-template-and-extracting-data_3.png)

- New OMR template can be created via button on top menu, toolbar icon, shortcut (**CTRL + N**), or File->New button.
- Existing OMR template can be loaded via button on main window, toolbar icon, shortcut (**CTRL + O**), using File->Open button or user can Drag & Drop the existing OMR template (.omr) file on the main window.
### **Load Template Image**
After template has been created, it is required to load a template image. It is the image that will be used to create the template markup.

Template image can be loaded via one of the following:

- Using Load Image button that is located at the center of window in application
- Application toolbar icon
- Edit->Load Template Image.. command or
- Drop image file using Drag & Drop

![todo:image_alt_text](creating-omr-template-and-extracting-data_4.png)
### **OMR Template Markup Creation**
After the image has been loaded, it is time to create the actual template markup. The markup is the process of adding special elements (OMR questions) over image, covering areas where respondents will be able to fill in marks. Hereby and further such areas will be referred to as OMR bubbles. Therefore your goal is to cover properly such bubbles with the rectangles provided by the application. Make sure you use various features to simplify this process, such as copy/paste, applying style of the selected element to all elements of the same type, shrinking, etc.

![todo:image_alt_text](creating-omr-template-and-extracting-data_5.png)

- Make sure to mark up every question on the page. When all questions are marked up, the stage may be considered as completed. Note that you can save template at any moment during markup creation (via toolbar, shortcuts and File->Save button).
- From toolbar, choose proper OMR elements to add. Currently, two types of OMR elements are available: 
  - **Choice box** - Use for simple question with more than one answer options
  - **Grid -** Use Grid for fields like ID, Name, etc. That means that you should choose Grid when you want to get complex value which consisting of some similar sections

![todo:image_alt_text](creating-omr-template-and-extracting-data_6.png)



![todo:image_alt_text](creating-omr-template-and-extracting-data_7.png)

- Place selected region of chosen OMR element over the drawn question using mouse click and dragging. After mouse is released, question is added to the specified area:

![todo:image_alt_text](creating-omr-template-and-extracting-data_8.png)

- Specify position and properties of the OMR element to neatly fit the drawn bubbles of the question being considered. For this purpose resize it with mouse. Also, make sure to edit amount of bubbles inside question, question name, key letters to be mapped on answers (e.g. A-E, 0-9, etc.)
- Bubbles area should be covered completely. Note that it is not necessary to cover exactly OMR element over bubbles, since on the next stage named **Template Correction**, these positions will be fixed automatically and neatly

![todo:image_alt_text](creating-omr-template-and-extracting-data_9.png)

![todo:image_alt_text](creating-omr-template-and-extracting-data_10.png)

![todo:image_alt_text](creating-omr-template-and-extracting-data_11.png)

- After one question has been created, utilize Copy/Paste functionality to ease and accelerate markup. The zoom commands as well as question alignment commands and other features can be used to make the markup process more convenient
- Elements snapping functionality also helps with precise positioning
- After you are done with creating the template markup, you need to go through one more stage to get images recognized: Template Validation. This stage are required to provide best recognition quality. You need to go through them only once per template
### **Template Validation**
- During the Template Validation the server side checks your markup and attempts to specify bubbles positions more accurately. The purpose of the stage is to validate the template and calculate the required data for the recognition step. The step serves to diagnose problems that may decrease the recognition quality
- Also during this stage user may be asked to pay attention to some elements that are considered to be problematic. For example, if the user placed the question where there was no actual bubble found the area will be highlighted



![todo:image_alt_text](creating-omr-template-and-extracting-data_12.png)

![todo:image_alt_text](creating-omr-template-and-extracting-data_13.png)

![todo:image_alt_text](creating-omr-template-and-extracting-data_14.png)

- To run the Template Validation simply click "Validate Template" button on toolbar. Your image and template markup will be sent to the server. It could take some time to get completed, because it includes interaction with the server and intensive computation on the server side. You should see busy indication while process is running. After the task has been done you should see slightly corrected positions of all elements within your markup. GUI will also display and highlight any problems that were detected
- When the result is received from the server, it’s time to fix your markup problems. You should see the hint if you have any problem, or whether you can go further to the next stage. Unfixed problems may affect the recognition quality. When you finished fixing them, it is required to run the validation step again
- If this step is completed with no errros you can go to the recognition stage
### **Recognition**
After template is created and prepared, the Recognition can be performed. To access Recognition tab you should either create and finalize template, or just load template that had been prepared and finalized previously.

- Press "Recognize" button to open Recognition tab
- At first you should load images that you want to be recognized according to the template. On the left side of Recognition view you can see panel where the load images and the load folder buttons are available. You can also use "Drag&Drop" to add images and folders

![todo:image_alt_text](creating-omr-template-and-extracting-data_15.png)

![todo:image_alt_text](creating-omr-template-and-extracting-data_16.png)

![todo:image_alt_text](creating-omr-template-and-extracting-data_17.png)

- Loaded images will be displayed as previews on the left and will be shown in full size at the center of the view
- You can remove or load more images via buttons on the bottom of the preview window and via toolbar buttons
- After image or images are loaded, you can send them for recognition. You can send either one specific image or a group of selected images. For the first option use small icon on the top right of the image preview (cloud icon). For the second one use toolbar button “Recognize”. You can also recognize all loaded images pressing “Recognize All Images” button at the toolbar
- Feel free to load both scanned images and photos

![todo:image_alt_text](creating-omr-template-and-extracting-data_18.png)

- You can also set your presets for preprocessing images to reduce traffic and costs

![todo:image_alt_text](creating-omr-template-and-extracting-data_19.png)



![todo:image_alt_text](creating-omr-template-and-extracting-data_20.png)

- After images queued for the recognition, they can be removed from this queue via cancel icon on the center of the image preview or via toolbar button “Cancel All”.
- The recognition operation for the image may take a couple of seconds. Busy indication will be displayed on the previews of images being processed.
- After image is processed, recognition results for that image will be shown on the right table. These results can be save as .csv file.
