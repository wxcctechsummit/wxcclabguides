---
title: "Lab 7: CRM Integration"
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

The object of this lab excercise is to Install and Configure the WebexCC Salesforce Agent Desktop Application
## Pre-requisite

1. Administrator/ Supervisor with Salesforce access​.
2. Administrator/ Supervisor with WebexCC portal access​.
3. New user (Agent) is already created​.
4. Agent is able to login to agent desktop​.
5. Agent should be part of a team​.
6. Basic knowledge of JSON format​.
7. Salesforce Custom Desktop Layout.
8. Use any online [JSON validator](https://jsonlint.com/) to validate the file​


### 1. Connector Installation From Salesforce AppExchange

  * Login to your Salesforce instance and Go to Setup
  * In the search box, type “AppExchange Marketplace”
  * In the AppExchange Marketplace type “Cisco Webex Contact Center for Salesforce”
  * Click Get It Now and choose either of the options to install
  * Install in Production—Choose when you've tested and is ready to go public.
  * Install in Sandbox—Choose when you've to test against a copy of the production org. The login URL is different for Sandbox environment. Once you've tested in the Sandbox, you must  install it on a production environment using the option Install in Production.
  * After the installation is complete, click Done.

### 2. Connector Installation Verification

 * In Salesforce navigate to Setup
 * In the search box, type “Installed Packages”
 * In the Installed Package List check for “Webex Contact Center”.
 * If found then Installation is successful

### 3. Salesforce Call Center Configuration

* In Salesforce navigate to Setup.
* In the search box, type “Call Centers”.
* Click the Edit link corresponding to the Webex Contact Center.
* Update the Display Name field if you want to change the Display name of the call center.
* Configure the CTI Adapter URL: https://desktop.wxcc-us1.cisco.com/
* Configure Softphone Layout:- Softphone Height: 600   Softphone Width: 550


### 4. Adding Call Center Users To Salesforce Call Center Application
* In Salesforce navigate to Setup.
* In the search box, type “Call Centers”.
* Click the link corresponding to the Webex Contact Center
* Click on the  “Manage Call Center Users”
* It opens the “Manage Users” page
* Click on “Add More Users” button to add users to call center application.  Click on “Remove Users” button to remove users from Call Center application.
* Search Screen opens and apply the filters to find the Call Center Users.
* Select the users from the list and click on the “Add to Call Center” button.
* It redirects to manage users page and it lists the all the users that are added to the call center application

### 5. Create Salesforce Softphone Layout Configuration

* In Salesforce navigate to Setup.
* In the search box, type “Softphone Layout”.
* Click on the “New” Button, it opens the “Softphone Layout Configuration page”. 
* Enter Name for the Softphone Layout Configuration. 
* Select the Is Default Layout Check Box If you want to make this Softphone layout default for all the call center application.
* Configure the Softphone and Screenpop settings for Inbound, Outbound and Internal Calls. 
* Click Save to create the Softphone Layout configuration

### 6. Salesforce Softphone Layout Assignment

* In Salesforce navigate to Setup.
* In the search box, type “Softphone Layout”.
* Click on the “Softphone Layout Assignment” Button, it opens the “Softphone Layout Assignment page”. 
* Assign the Softphone Layout configuration for each user profiles


### 7. Salesforce Task Layout Configuration 

* In Salesforce navigate to Setup.
* In the search box, type “Object Manager” and click on “Object Manager” link button. 
* It opens the Object Manager list page. Filter the list page by typing “Task” in the Search box. Click on “Task” button link
* It opens the Task Details page. Select the page layout.  
* Click Page Layout Assignment > Edit Assignment.
* Select a profile from the displayed list in the Profiles column.
* Select the Cisco Webex Contact Center Task Layout from the Page Layout To Use drop-down list.
* Click Save to assign the Task Layout

### 8. WebexCC Salesforce Desktop Report View 

* In Salesforce, click App Launcher > Webex Contact Center.
* From the Navigation Apps drop-down, select Reports. Note: If the reports is not listed, click Edit > Add More Items and add the Reports
* To see all the existing reports, click All Reports. Note:There is a default call activity report that installs with Cisco Webex Contact Center for Salesforce client.
* In the search box, type “Object Manager” and click on “Object Manager” link button. 

### 9. WebexCC Salesforce Desktop Layout Configuration 

* Login to WebexCC Admin Portal
* Go to Provisioning >  Desktop Layout > New Layout
* Enter Name and Description for the desktop layout.
* Status by default will be Active. 
* Add the Teams to Desktop layout. Agents associated with that team will get the Salesforce Desktop Layout.
* Upload the custom desktop layout for WebexCC Salesforce Desktop.
* Click Save.A custom Desktop Layout named Salesforce has been created in WebexCC.

