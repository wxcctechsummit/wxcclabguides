---
title: "Lab 6: CRM Integration"
---

# WebexCC Salesforce Agent Desktop Installation And Configuration

Video example


<iframe width="1024" height="576" src="https://youtube.com/embed/VQuxq5yGo2M?rel=0" title="CRM Integration" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents

- [1. Connector Installation From Salesforce AppExchange](#1-connector-installation-from-salesforce-appexchange)
- [2. Connector Installation Verification](#2-connector-installation-verification)
- [3. Salesforce Call Center Configuration](#3-salesforce-call-center-configuration)
- [4. Adding Call Center Users To Salesforce Call Center Application](#4-adding-call-center-users-to-salesforce-call-center-application)
- [5. Create Salesforce Softphone Layout Configuration](#5-create-salesforce-softphone-layout-configuration)
- [6. Salesforce Softphone Layout Assignment](#6-salesforce-softphone-layout-assignment)
- [7. Salesforce Task Layout Configuration](#7-salesforce-task-layout-configuration)
- [8. WebexCC Salesforce Desktop Report View](#8-webexcc-salesforce-desktop-report-view)
- [9. WebexCC Salesforce Desktop Layout Configuration](#9-webexcc-salesforce-desktop-layout-configuration)

# Introduction

## Lab Objective

The object of this lab excercise is to Install and Configure the WebexCC Salesforce Agent Desktop Application.

## Pre-requisites

1. Administrator/ Supervisor with Salesforce access​.
2. Administrator/ Supervisor with WebexCC portal access​.
3. New user (Agent) is already created​.
4. Agent is able to login to agent desktop​.
5. Agent should be part of a team​.
6. Basic knowledge of JSON format​.
7. Salesforce Custom Desktop Layout.
8. Use any online [JSON validator](https://jsonlint.com/) to validate the file​.


### 1. Connector Installation From Salesforce AppExchange

- Login to your [Salesforce](https://login.salesforce.com) instance and go to `Setup`.
- In the search box, type `AppExchange Marketplace`.
- In the AppExchange Marketplace type `Cisco Webex Contact Center for Salesforce`.
- Click on the Cisco Webex Contact Center App and the click on `Get It Now`.
- On the pop-up window, click on `Open Login Screen`. If prompted, login again with your credentials and `Allow` access to the **appx_api**.
- After verifying your login, choose the `Intall in This Org` option.
- Fill in the required fields with your details and accept the Terms and Conditions to be able to proceed with installation.
- Choose `Install for All Users` option and then click on `Install`.
- If asked, grant access to third party web site _cpc.ccone.net_ by clicking on the checkbox and then on `Continue`. 
- After the installation is complete, click `Done`.

### 2. Connector Installation Verification

- In Salesforce, navigate to `Setup`.
- In the search box, type `Installed Packages`.
- In the Installed Packages list, check for `Webex Contact Center`.
- If found, then installation was successful.

### 3. Salesforce Call Center Configuration

- In Salesforce, navigate to `Setup`.
- In the search box, type `Call Centers` and click on `Continue`.
- Click the `Edit` link corresponding to the `Webex Contact Center Agent Desktop`.
- Click on `Edit` to set up the CTI settings.
- Update the `Display Name` field if you want to change the Display name of the call center.
- Configure the following CTI Adapter URL: https://desktop.wxcc-us1.cisco.com/ .
- Configure **Softphone Height: 600** and **Softphone Width: 550**. 


### 4. Adding Call Center Users To Salesforce Call Center Application
- In Salesforce navigate to Setup.
- In the search box, type “Call Centers”.
- Click the link corresponding to the Webex Contact Center.
- Click on `Manage Call Center Users` to pen the Manage Users page.
- Click on `Add More Users` button to add users to Call Center application.
- `Search for New Users` page opens where you can apply filters to find Call Center users. Click on `Find` to list all the available users.
- Select your user from the list and click on the `Add to Call Center` button.
- You will be redirected to the `Manage Users` page, where your user should now be listed.

### 5. Create Salesforce Softphone Layout Configuration

- In Salesforce, navigate to `Setup`.
- In the search box, type `Softphone Layout` and click on `Continue`.
- Click on the `New` button to open the `Softphone Layout Configuration page` and create a softphone layout to use as **default**. 
- Enter a `Name` for the Softphone Layout Configuration. 
- Select the `Is Default Layout` checkbox to make this Softphone layout default for all the call center application.
- On the `salesforce.com objects`, remove `Lead` from the selections and add `Opportunity`.
- On the `Screen Pop Settings`, choose `Pop to new Contact` for **No matching records**, `Pop detail page` for **Single-matching records** and `Pop to search page` for **Multiple-matching records**.
- Click `Save` to create the Softphone Layout configuration.

### 6. Salesforce Softphone Layout Assignment

- If not already there, in the search box type `Softphone Layout` and click on `Continue` to reach the Softphone Layout page.
- Click on the `Softphone Layout Assignment` Button, it opens the “Softphone Layout Assignment page”. 
- Assign the Softphone Layout configuration you created to the `System Administrator` profile.
- Click `Save` to assign the Softphone Layouts.

### 7. Salesforce Task Layout Configuration 

- In Salesforce, navigate to `Setup`.
- In the search box, type `Object Manager` and click on it. 
- Filter the list page by typing `Task` in the `Quick Find` search box and click on the Task button link.
- Select `Page Layouts` on the left of the Task details page.
- Click on `Page Layout Assignment` on top-right and then on `Edit Assignment`.
- Select the `System Administrator` profile from the displayed list in the Profiles column.
- Select the `Cisco Webex Contact Center Task Layout` from the `Page Layout To Use` drop-down list on top.
- Apply the same page layout to `Standard User` and `Standard Platform User` profiles as well.
- Click `Save` to assign the Task Layout.

### 8. WebexCC Salesforce Desktop Report View 

- In Salesforce, click `App Launcher` on top left and then choose `Webex Contact Center`.
- From the Navigation Apps drop-down list, select `Reports`. **Note:** If Reports is not listed, click `Edit` > `Add More Items` and add the `Reports`.
- To see all the existing reports, click `All Reports`. **Note:** There is a default call activity report that installs with Cisco Webex Contact Center for Salesforce client.

### 9. WebexCC Salesforce Desktop Layout Configuration 

- Login to [WebexCC Admin Portal](https://portal.wxcc-us1.cisco.com/portal/home.html).
- Go to `Provisioning` >  `Desktop Layout` > `New Layout`.
- Enter Name and Description for the desktop layout.
- Status by default will be `Active`. 
- Add the `Teams` to Desktop layout. Agents associated with that team will get the Salesforce Desktop Layout.
- Upload the custom desktop layout for WebexCC Salesforce Desktop.
- Click `Save`. This will create a custom Desktop Layout named Salesforce in WebexCC.

**Congratulations!  **CRM Integration lab is now complete!**

[Back to top](#table-of-contents)

---

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/TechSummitRoW_2021/HomePage.html";}
function nextLab() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/TechSummitRoW_2021/Lab7.html";}
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
  padding: 10px;">Next Lab 7: Google CCAI Integration</button>

</div>

