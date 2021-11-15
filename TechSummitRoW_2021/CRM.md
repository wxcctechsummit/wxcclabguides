---
title: "Lab 4: CRM Integration"
---


# Introduction

### Lab Objective

This lab covers Webex Contact Center Agent Desktop integration with the most popular CRM solutions (Salesforce and Microsoft Dynamics 365) which allows you to launch the Agent Desktop from within the CRM, providing an integrated Agent Experience for inbound and outbound calls.


# Table of Contents

[4.1 Salesforce integration](#41-salesforce-integration)
- [Optional: Salesforce Account Creation](#optional-create-salesforce-account)
- [Part 1: Connector Installation](#part-1-connector-installation)
    * [1. Connector Installation From Salesforce AppExchange](#1-connector-installation-from-salesforce-appexchange)
    * [2. Connector Installation Verification](#2-connector-installation-verification)
- [Part 2: Call Center Configuration](#part-2-call-center-configuration)
    * [3. Salesforce Call Center Configuration](#3-salesforce-call-center-configuration)
    * [4. Adding Call Center Users To Salesforce Call Center Application](#4-adding-call-center-users-to-salesforce-call-center-application)
- [Part 3: Softphone & Task Layout Configuration](#part-3-softphone-task-layout-configuration)
    * [5. Create Salesforce Softphone Layout Configuration](#5-create-salesforce-softphone-layout-configuration)
    * [6. Salesforce Softphone Layout Assignment](#6-salesforce-softphone-layout-assignment)
    * [7. Salesforce Task Layout Configuration](#7-salesforce-task-layout-configuration)
- [Part 4: Reports](#part-4-reports)
    * [8. WebexCC Salesforce Desktop Report View](#8-webexcc-salesforce-desktop-report-view)
- [Part 5: WebexCC Desktop Layout](#part-5-webexcc-dekstop-layout)
    * [9. WebexCC Salesforce Desktop Layout Configuration](#9-webexcc-salesforce-desktop-layout-configuration)
- [Login Agent and Make a Test Call](#login-agent-make-call)

[4.2 Microsoft Dynamics 365 integration](#42-microsoft-dynamics-365-integration)


# 4.1 Salesforce integration

### Pre-requisites

1. Administrator/ Supervisor with Salesforce access​.
2. Administrator/ Supervisor with WebexCC portal access​.
3. New user (Agent) is already created​.
4. Agent is able to login to agent desktop​.
5. Agent should be part of a team​.
6. Basic knowledge of JSON format​.
7. Salesforce Custom Desktop Layout.
8. Use any online [JSON validator](https://jsonlint.com/) to validate the file​.
9. Lab 2 (IVR and Contact Routing) completed.


## Optional: Create Salesforce Account

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/_4ZgHUSsp4U?rel=0" title="CRM Integration Lab: Salesforce Account Creation" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


- Navigate to [Salesforce Developer](https://developer.salesforce.com) website and click on **Sign Up**.

- Complete the form with your personal details and click on **Sign me up** to create your account.

> **Note:** Username needs to be in the form of an e-mail address. This address does not need to be a real e-mail address.

- Go to your e-mail inbox and wait for the confirmation e-mail regarding your account. Click on **Verify Account**.

- Enter a **password** as well as an **answer** to the security question. This will successfully create your account and log you in the Salesforce platform.


## Part 1: Connector Installation

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/T1MQ161bTSs?rel=0" title="CRM Integration Lab Part 1: Connector Installation" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
 
### 1. Connector Installation From Salesforce AppExchange

- Login to your [Salesforce](https://login.salesforce.com) instance and go to **Setup**.

- In the search box, type `AppExchange Marketplace`.

- In the AppExchange Marketplace type `Cisco Webex Contact Center for Salesforce`.

- Click on the Cisco Webex Contact Center App and the click on **Get It Now**.

- On the pop-up window, click on **Open Login Screen**. If prompted, login again with your credentials and **Allow** access to the `appx_api`.

- After verifying your login, choose the **Intall in This Org** option.

- Fill in the required fields with your details and accept the Terms and Conditions to be able to proceed with installation.

- Choose **Install for All Users** option and then click on **Install**.

- If asked, grant access to third party web site `_cpc.ccone.net_` by clicking on the checkbox and then on **Continue**. 

- After the installation is complete, click **Done**.

### 2. Connector Installation Verification

- In Salesforce, navigate to **Setup**.

- In the search box, type `Installed Packages`.

- In the Installed Packages list, check for **Webex Contact Center**.

- If found, then installation was successful.


## Part 2: Call Center Configuration

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/-pKYj1z2E7U?rel=0" title="CRM Integration Lab Part 2: Call Center Configuration" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 3. Salesforce Call Center Configuration

- In Salesforce, navigate to **Setup**.

- In the search box, type `Call Centers` and click on **Continue**.

- Click the **Edit** link corresponding to the **Webex Contact Center Agent Desktop**.

- Click on **Edit** to set up the CTI settings.

- Update the **Display Name** field if you want to change the Display name of the call center.

- Configure the following CTI Adapter URL: https://desktop.wxcc-us1.cisco.com/ .

- Configure `Softphone Height: 600` and `Softphone Width: 550`. 

- Click **Save**


### 4. Adding Call Center Users To Salesforce Call Center Application

- Click on **Manage Call Center Users** to open the Manage Users page.

- Click on **Add More Users** button to add users to Call Center application.

- **Search for New Users** page opens where you can apply filters to find Call Center users. Click on **Find** to list all the available users.

- Select your user from the list and click on the **Add to Call Center** button.

- You will be redirected to the **Manage Users** page, where your user should now be listed.


## Part 3: Softphone & Task Layouts

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/w0tCjlyEWEY?rel=0" title="CRM Integration Lab Part 3: Softphone & Task Layouts" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 5. Create Salesforce Softphone Layout Configuration

- In Salesforce, navigate to **Setup**.

- In the search box, type `Softphone Layout` and click on **Continue**.

- Click on the **New** button to open the **Softphone Layout Configuration page** and create a softphone layout to use as `default`.
 
- Enter a `Name` for the Softphone Layout Configuration. 

- Select the **Is Default Layout** checkbox to make this Softphone layout default for all the call center application.

- On the **salesforce.com objects**, remove `Lead` from the selections and add `Opportunity`.

- On the **Screen Pop Settings**, choose `Pop to new Contact` for **No matching records**, `Pop detail page` for **Single-matching records** and `Pop to search page` for **Multiple-matching records**.

- Click **Save** to create the Softphone Layout configuration.

### 6. Salesforce Softphone Layout Assignment

- If not already there, in the search box type `Softphone Layout` and click on **Continue** to reach the Softphone Layout page.

- Click on the **Softphone Layout Assignment** Button, it opens the Softphone Layout Assignment page. 

- Assign the Softphone Layout configuration you created to the **System Administrator** profile.

- Click **Save** to assign the Softphone Layouts.

### 7. Salesforce Task Layout Configuration 

- In Salesforce, navigate to **Setup**.

- In the search box, type `Object Manager` and click on it. 

- Filter the list page by typing `Task` in the **Quick Find** search box and click on the **Task button link**.

- Select **Page Layouts** on the left of the Task details page.

- Click on **Page Layout Assignment** on top-right and then on **Edit Assignment**.

- Select the **System Administrator** profile from the displayed list in the Profiles column.

- Select the **Cisco Webex Contact Center Task Layout** from the **Page Layout To Use** drop-down list on top.

- Apply the same page layout to **Standard User** and **Standard Platform User** profiles as well.

- Click **Save** to assign the Task Layout.


## Part 4: Reports

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/jLw92srDV2I?rel=0" title="CRM Integration Lab Part 4: Reports" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 8. WebexCC Salesforce Desktop Report View 

- In Salesforce, click **App Launcher** on top left and then choose **Webex Contact Center**.

- From the Navigation Apps drop-down list, select **Reports**.

> **Note:** If Reports is not listed, click **Edit** > **Add More Items** and add the **Reports**.

- To see all the existing reports, click **All Reports**. 

> **Note:** There is a default call activity report that installs with Cisco Webex Contact Center for Salesforce client.


## Part 5: WebExCC Salesforce Desktop Layout

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/wCzcAIL6w3Y?rel=0" title="CRM Integration Lab Part 5: WebExCC Salesforce Desktop Layout" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 9. WebexCC Salesforce Desktop Layout Configuration 

- Login to [WebexCC Admin Portal](https://portal.wxcc-us1.cisco.com/portal/home.html).

- Go to **Provisioning** >  **Desktop Layout** > **New Layout**.

- Enter Name and Description for the desktop layout.

- Status by default will be **Active**. 

- Add the **Teams** to Desktop layout. Agents associated with that team will get the Salesforce Desktop Layout.

- Upload the custom desktop layout for WebexCC Salesforce Desktop.
[WebexCC_Salesforce_Desktop.zip](https://github.com/wxcctechsummit/wxcclabguides/raw/08fb8082092b2552ec89e1b42dbe84b12214a805/WebexCC_Salesforce_Desktop.zip)

- Click **Save**. This will create a custom Desktop Layout named Salesforce in WebexCC.

## Login Agent and Make a Test Call

- Back on Salesforce page, click on **App Launcher** icon on top left and then click on **Webex Contact Center**.

- On the bottom left, click on **Phone** and then **Sign In**.

- Sign in an agent that is part of the team that the Dekstop Layout was associated with previously. You can use the agent, EPs and flow created in Lab 2 Part 2 (IVR and Contact Routing) for the queued to agent scenario.

- Make sure the agent is in available state and make a test call to your EP.

- Upon accepting the call, we will see account information populated for this call. A `task activity` should also be created and visible upon accepting the call. 


# 4.2 Microsoft Dynamics 365 integration

### Pre-requisites

1. Access to a Webex Contact Center instance
2. Administrator access to the organization on [Control Hub](https://admin.webex.com/) and [Webex Contact Center Management Portal](https://portal.wxcc-us1.cisco.com/). 
3. An Agent account with access to the [Desktop](https://desktop.wxcc-us1.cisco.com/).
4. An MS Dynamics Sales instance. For specifics, refer the next section "Start Microsoft Dynamics Trial"
5. Access to the [Webex Contact Contact Center Desktop Layout for Microsoft Dynamics](https://github.com/CiscoDevNet/webex-contact-center-widget-starter/tree/master/Examples/Layouts/MS Dynamics/) JSON.
6. Lab 2 (IVR and Contact Routing) completed.


## Optional: Start Microsoft Dynamics Trial

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/p2KYPe1LAYs?rel=0" title="CRM Integration Lab: Start Microsoft Dynamics Trial" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## Install applications within MS Dynamics 365

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/h3RWXoFZDJg?rel=0" title="CRM Integration Lab: Install applications within MS Dynamics 365" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## Configure applications within MS Dynamics 365

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/Ku3-ek0o4_0?rel=0" title="CRM Integration Lab: Configure applications within MS Dynamics 365" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## Test Webex Contact Center Agent Desktop embedded into MS Dynamics

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/PVJiQeNd2NQ?rel=0" title="CRM Integration Lab: Test Webex Contact Center Agent Desktop embedded into MS Dynamics" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### **Congratulations! CRM Integration lab is now complete!**

[Back to top](#table-of-contents)

---

### Congratulations, you have compleated Lab 4 tasks! 
### We would like to keep track of your progress and make sure that we are giving you effective support. Please take approximately one minute to complete the short survey.


<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/TechSummitRoW_2021/HomePage.html";}
function nextLab() 
 {
 window.open("https://app.smartsheet.com/b/form/42c2c1f4e71940088ad0ea8053ac3006", '_blank');
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/TechSummitRoW_2021/CCAI.html";
 }
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
  padding: 10px;">Take Survey and Go to Lab 5</button>

</div>
