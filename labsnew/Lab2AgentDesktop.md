---
title: 'Lab 2: Customizing Agent Desktop'
---

# Custom Desktop Layout

Video example

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/ZYFwqEjZLWM?rel=0" title="WxCC Customizing Agent Desktop Lab" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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

## Quick Links

- <a href="https://portal.wxcc-us1.cisco.com/portal" target="_blank">Portal</a>
- <a href="https://analyzer.wxcc-us1.cisco.com/analyzer/home" target="_blank">Analyzer</a>
- <a href="https://desktop.wxcc-us1.cisco.com" target="_blank">Agent Desktop</a>

### 1. Download default desktop Layout

- Login to [WxCC portal](https://portal.cjp.cisco.com/portal/home.html) with admin credentials​
  - Note that you should have at least one agent configured for testing at this point
- Navigate to Provisioning --> Desktop Layout​
- Click on ellipses `...` of Global Layout to edit [Video Direct Link](https://www.youtube.com/embed/ZYFwqEjZLWM?start=150)
- Now click on edit
- Click on download button ​
- Download the Default Desktop Layout.json file​
- Now cancel out, as you only need to get the JSON file

### 2. Customize default desktop layout with logo and title

- Open the Default Layout JSON in any text editor e.g. Notepad or Sublime text.​
- Modify the value of appTitle key to change Agent Desktop title ​
- Modify the value of logo key as your company logo URL or use this dummy url: https://widget-kad.s3.amazonaws.com/Logos/boscologo5.png
- “Save As” the JSON file with a distinguishable name.

### 3. Upload the custom desktop layout an verify

- Login to [WxCC portal](https://portal.cjp.cisco.com/portal/home.html) with admin credentials​
- Navigate to Provisioning --> Desktop Layout​
- Click on New Layout
- Provide any preferable name and description ​
- Click on Team textbox to add the team ​
- Click Upload button to upload the modified JSON file​
- Click Save button to apply the layout.
- Login/Reload [WxCC agent desktop](https://desktop.wxcc-us1.cisco.com) to verify the layout

### 4. Assign header widget and nav bar widget

- Open the layout JSON file in any text editor e.g.
- Notepad or Sublime text.(be careful copying from PowerPoint might add unwanted spaces/characters... causing the JSON to \* \* fail on load) use an online [JSON formatter](https://jsonformatter.org/) to clean up if required.​
- Modify the header section as mentioned in video
- Modify the navigation section by creating a new navigation widgit with a direct link​ [Video Direct Link](https://www.youtube.com/embed/ZYFwqEjZLWM?start=330)
- “Save As” the JSON file with a unique preferable name

### 5. Upload the modified layout

- Login to [WxCC portal](https://portal.cjp.cisco.com/portal/home.html) with admin credentials​
- Navigate to Provisioning --> Desktop Layout​
- Search for your layout ​
- Click on ... to edit the existing layout​
- Now click on edit
- Click Upload button to upload the modified JSON file​
- Finally click Save button to apply the layout.

### 6. Verify the layout

- Login/Reload [WxCC agent desktop](https://desktop.wxcc-us1.cisco.com) to verify the layout

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LabLibrarynew";}
</script>

<div id="button-row">
	<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go back to Main Page</button>

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Next Lab 3: IVR and Contact Routing</button>

</div>
