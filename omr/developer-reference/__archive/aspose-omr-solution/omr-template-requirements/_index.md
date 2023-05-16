---
title: "OMR Template Requirements"
type: docs
url: /omr-template-requirements/
weight: 40
---

{{% alert color="primary" %}} 

Aspose.OMR client application is a tool to create OMR templates and to extract data entered into forms such as consumer surveys, assessment sheets etc. This article describes the details that are necessary for OMR Template Editor (client) tool.

{{% /alert %}} 
## **Template Requirements**
Following are the recommendations for achieving better results with the API.
### **Using Original OMR Sheet Image**
Use original OMR sheet image to create OMR template. Scanned image is not recommended at all.
### **Bubbles with High Contrast Borders**
Bubbles should have clear high contrast borders. This actually represents the ratio of border pixel value to its background averaged by whole bubble contour. For example, if bubble border intensity is 50 and average background intensity is 200, then the contrast ratio is 1 to 4. The greater the intensity gap, the higher the contrast. We suggest that scanned OMR sheet image contrast ratio should be (at least) equal to proportion of 1 to 2. Lesser ratio e.g. 1 to 1.3 can be processed only if filled mark area (bubble) have sharp borders and is not stuck together or to any background object.
### **Sharp or Clear Borders**
Sharp or clear border means that the border is not corrupt / distorted or blurred. This also implies that values of filled pixels must differ from background. In case an image has high noise, it would be impossible for API to process the mark. Marked area should be closed and well distinguished from other static objects on the template. Developers may use circles, ellipses, rectangles or other convex polygons to define optical mark (bubble).
### **Form factor of Bubbles**
It is always recommended to use bubbles of same form, size and thickness in a template. Avoid using bubbles of different sizes. Both OMR template and user pictures are processed in gray using primitive algorithm of averaging. In case heavy color contrast has been used in the OMR sheet image, this would require developer to perform gray transformation by himself.
## **Reference Points Requirements**
The usage of reference points is always an option. In such case:

- Make the reference points at least two times bigger than bubbles. For example, rectangular reference points ought to be at least 3mm for the smallest side and at least 6mm for the longest side. 
- Reference points of any shape can be used provided these are well distinguished from other static objects on the template
- It's assumed that rectnagles be filled up with black with high contrast 
- Reference points should be distributed uniformly over template for robust matching, even in case where paper is crumpled. Too many reference points will slow down the matching process. Putting at least 4 points at the border of OMR template in every corner is recommended.
- Putting all the points in one row or column should be avoided as it leads to offset in one direction
- It’s assumable to use rectangles filled up with black. Make them as much contrast as possible. Position could be chosen arbitrary, but you should put reference points at the border of OMR template in its every corner. Put in at least 4. The more you have reference points uniformly distributed over template the more robust matching will be, especially when paper was crumpled. Avoid putting too much, because that will slow down matching. Avoid placement almost of all the points in one row or column, because such arrangement leads to offset in one direction.
## **Scan/photo Requirements**
The general requirements for Scanned image are as follow:

- It is strongly recommend to use scanned image of at least 150 DPI 
- Bubbles size could be 3mm (30 pix) or bigger
- Bubble border should be at least 0.3 mm (3 pix) thick or bigger
- Be sure to have enough free space around the border, at least triple the thickness between bubbles or high contrast background objects (i.e. 0.9mm/10 pix).
- Images can be rotated within 0 to 25 degrees
- Perspective corruption should be within certain limits. Ratio of paper sides can not differ more than 1.4 times. Thus, A4 paper sheet has ratio 70/99 (about 0.71). The corrupted document ratio should be within the range of 0.51 to 0.98.
- Recommended height and width for images is maximum up to 5000 pixels. This is because there are no benefits in recognizing such large images and it will take more time and resources to process the scanned OMR sheet.
## **Marks Requirements**
Results of recognition process highly depend on quantitative and qualitative indicators of filling. If background is not uniform, especially inside bubbles, binarization may perform badly. In such case, developer has to provide binarization transformation for his template. Bubbles on the OMR sheet must be filled up to 75%.
