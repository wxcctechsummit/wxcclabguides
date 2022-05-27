---
title: "Lab 3: Agent Desktop"
---

# Custom Desktop Layout

Video example

<iframe width="560" height="315" src="https://www.youtube.com/embed/KZgUvCKh284" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents

- [1. Download default desktop Layout](#1-download-default-desktop-layout)
- [2. Customize default desktop layout with logo and title](#2-customize-default-desktop-layout-with-logo-and-title)
- [3. Upload the custom desktop layout an verify](#3-upload-the-custom-desktop-layout-an-verify)
- [4. Assign header widget and nav bar widget](#4-assign-header-widget-and-nav-bar-widget)
- [5. Upload the modified layout](#5-upload-the-modified-layout)
- [6. Verify the layout](#6-verify-the-layout)

# Introduction

## Lab Objective

The object of this lab excercise is to customize the logo and title of the agent desktop and also add widget in the header section and nav bar section.
## Pre-requisite

1. Administrator/ Supervisor with portal access​.
2. New user (Agent) is already created​.
3. Agent is able to login to agent desktop​.
4. Agent should be part of a team​.
5. Basic knowledge of JSON format​
6. Use any online [JSON validator](https://jsonlint.com) to validate the file​


### 1. Download default desktop Layout

  * Login to [WxCC portal](https://portal.cjp.cisco.com/portal/home.html) with admin credentials​
  * Navigate to Provisioning --> Desktop Layout​
  * Click on ellipses (...) of Global Layout to edit ​
  * Now click on edit
  * Click on download button ​
  * Download the Default Desktop Layout.json file​
  * Now cancel out, as you only need to get the JSON file


### 2. Customize default desktop layout with logo and title

 * Open the Default Layout JSON in any text editor e.g. Notepad or Sublime text.​
 * Modify the value of appTitle key to change Agent Desktop title (Refer Pic-1).​
 * Modify the value of logo key as your company logo URL or use this dummy url: https://widget-kad.s3.amazonaws.com/Logos/boscologo5.png
 * “Save As” the JSON file with a distinguishable name.


### 3. Upload the custom desktop layout an verify

* Login to [WxCC portal](https://portal.cjp.cisco.com/portal/home.html) with admin credentials​
* Navigate to Provisioning --> Desktop Layout​
* Click on New Layout
* Provide any preferable name and description ​
* Click on Team textbox to add the team ​
* Click Upload button to upload the modified JSON file​
* Click Save button to apply the layout.
* Login/Reload [WxCC agent desktop](https://desktop.wxcc-us1.cisco.com) to verify the layout 


### 4. Assign header widget and nav bar widget
* Open the layout JSON file in any text editor e.g. 
* Notepad or Sublime text.(be careful copying from PowerPoint  might add unwanted spaces/characters... causing the JSON to * * fail on load) use an online [JSON formatter](https://jsonformatter.org/) to clean up if need be.​
* Modify the header section as mentioned in video
* Modify the navigation section as mentioned below​
* “Save As” the JSON file with a unique preferable nam

### 5. Upload the modified layout

* Login to [WxCC portal](https://portal.cjp.cisco.com/portal/home.html) with admin credentials​
* Navigate to Provisioning --> Desktop Layout​
* Search for your layout ​
* Click on ... to edit the existing layout​
* Now click on edit
* Click Upload button to upload the modified JSON file​
* Finally click Save button to apply the layout.

### 6. Verify the layout 

* Login/Reload [WxCC agent desktop](https://desktop.wxcc-us1.cisco.com) to verify the layout 



Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Sameer Yadav (sameyada) | 08 Jan 2021 |

