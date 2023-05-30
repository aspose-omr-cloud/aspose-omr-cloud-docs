---
weight: 10
date: "2023-04-21"
author: "Vladimir Lapin"
type: docs
url: /txt-markup/
feedback: OMRCLOUD
title: Text markup
description: Lightweight markup language for machine-readable OMR forms specifically tailored for Aspose.OMR Cloud.
keywords:
- layout
- markup
- template
- design
- form
- text
- txt
---

Aspose.OMR Cloud **text markup** is a lightweight markup language specifically tailored for describing content and layout of machine-readable OMR forms. It is content-focused, with minimal number of tags or formatting instructions.

The downsides of text markup are that it does not support syntax highlighting and is somewhat harder to read when working with nested elements.

Template sources are stored as plain-text files that can be opened with any general-purpose text editor or code editor (such as Atom, Notepad, Visual Studio Code, and so on). The following encodings are supported:

- **UTF-8** - can accommodate forms in any combination of natural languages, including Chinese, Arabic, Hindi, Hebrew, and more. The file can be with or without a BOM (byte order mark).
- **ANSI** - only supports Western European characters and numbers.

You can use Windows (_CRLF_), Unix (_LF_) and Mac OS 9 (_CR_) line endings.

## Elements

**Text** markup includes a wide range of elements that allow you to create machine-readable OMR forms of any complexity - from a simple survey to high school exam papers, checklists and ballots.

- [Layout](/omr/txt-markup/elements-layout/)  
  Arrange other elements; define the appearance and design of machine-readable forms.
- [Questionnaires](/omr/txt-markup/elements-questionnaire/)  
  Build machine-readable surveys, ballots, checklists, and similar forms.
- [Answer sheets](/omr/txt-markup/elements-bubble-matrix/)  
  Populate a form with a grid of bubbles representing answers to an exam, test, or assessment.
- [Barcodes and QR codes](/omr/txt-markup/elements-barcode/)  
  Add barcodes and QR-codes to personalize or uniquely identify a form.
- [Write-ins](/omr/txt-markup/write_in/)  
  Provide a blank field in which the respondent can hand write some text or draw a picture.
