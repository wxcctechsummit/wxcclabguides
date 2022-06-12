---
title: 'Lab 4: Facebook Messenger Configuration'
---


# Table of Contents
- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
    - [Lab Objective](#lab-objective)
    - [Pre-requisite](#pre-requisite)
    - [Quick Links](#quick-links)
- [Lab Section](#lab-section)
  - [Step 1 Facebook Page configuration](#step-1-facebook-page-configuration)
  - [Step 2. Facebook Messenger Asset creation & register to Webex CC](#step-2-facebook-messenger-asset-creation--register-to-webex-cc)
  - [Step 3. Create Entry Point and Queue](#step-3-create-entry-point-and-queue)
    - [1. Create Entry Point in Management Portal](#1-create-entry-point-in-management-portal)
    - [2. Create Queue in Management Portal](#2-create-queue-in-management-portal)
  - [Step 4. Create/Upload Facebook Messenger flow](#step-4-createupload-facebook-messenger-flow)
    - [1. Initial flow loading](#1-initial-flow-loading)
    - [2. Start node and Custom Variables](#2-start-node-and-custom-variables)
    - [3. Edit Queue Task node](#3-edit-queue-task-node)
  - [Step 5. Verification - start Facebook Chat and accept the request](#step-5-verification---start-facebook-chat-and-accept-the-request)
  - [Back to top](#back-to-top)
    - [Congratulations, you have completed this section!](#congratulations-you-have-completed-this-section)


# Introduction

### Lab Objective

In this Lab, we will go through the tasks that are required to complete the basic Facebook Messenger (FBM) integration. You will be able to initiate a Facebook contact to the Contact Center from Facebook Messenger and be able to accept/respond to the contact by logging in as an agent.  

In this lab you you will be configuring Service, Chat Assets, Entry Point, Queue, Chat Template, Website Settings, and corresponding workflows.


### Pre-requisite

1. You received an admin credentials to configure in Management Portal and Webex Connect.
2. You have successfully completed the previous Lab **Preconfiguration**
3. You have a Facebook Account

### Quick Links

> Control Hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="_blank"}**\
> Workflows: **[GitHub page](https://github.com/CiscoDevNet/webexcc-digital-channels){:target="_blank"}**\
> Connect: https://cl1pod**\<ID\>**.imiconnect.io/ (where **\<ID\>** is your POD number)

# Lab Section

## Step 1 Facebook Page configuration

- Customer/Partner should have a Facebook account to create a Facebook Business page

- Login to Facebook and create a business page that can be used in WxCC for polling and handling the messenger chats Additional details of facebook page setup is available here: [Facebook Business page setup](https://www.facebook.com/business/pages/set-up)){:target="_blank"}**\


- Click on `Create a Page` button

<img align="middle" src="images/Lab4_4.jpg" width="1000" />

- If you are logged in already to Facebook, you will be presented with the Business Page creation tool. Simply give the page a Name and a Category then Click `Create Page` button
<img align="middle" src="images/Lab4_5.jpg" width="1000" />

[Back to top](#table-of-contents)

## Step 2. Facebook Messenger Asset creation & register to Webex CC

- Login to your respective Webex Connect UI using the provided URL https://cl1pod**X**.imiconnect.io/ (where **X** is your POD number).

- Navigate to `Assets` > `Apps` > `Configure New App` > `Messenger` and Click on `Add Messenger Page` button
<img align="middle" src="images/Lab4_1.gif" width="1000" />

- If you haven't done already, authenticate with your FB account where you have a page already created. Then select the respective page that you want to integrate
<img align="middle" src="images/Lab4_6.jpg" width="1000" />

- Accept all default permissions
  <img align="middle" src="images/Lab4_7.jpg" width="1000" />

- That completes the linking of the Facebook connect with Webex Connect
  <img align="middle" src="images/Lab4_8.jpg" width="1000" />

- Finally select the Business Page you want to link to the Asset
  <img align="middle" src="images/Lab4_9.jpg" width="1000" />

-  Provide the name and click `Save`
  <img align="middle" src="images/Lab4_10.jpg" width="1000" />

-  Click `Register to Webex CC`  in the ‘Configure New App-Messenger’ window ->  In the resulting window select the service and click `Register`.
  <img align="middle" src="images/Lab4_11.jpg" width="1000" />

- Confirm that registration with Webex CC completed successfully
  <img align="middle" src="images/Lab4_12.jpg" width="1000" />

- Scroll down and take note of the M.ne link in the `Page Discovery Addons` section. We will use that link to trigger the Facebook Messenger interaction from the Customer end. Also take note of the numeric string paramenter in the m.me link. That's the `Facebook Page ID` which we will also need later when configuring the flow.

  <img align="middle" src="images/Lab4_16.jpg" width="1000" />

- Click on the back arrow to go back to the list of Assets Apps. Then take note of the application ID (app id) we just created. We will also need that app ID in the flow

  <img align="middle" src="images/Lab4_15.jpg" width="1000" />

[Back to top](#table-of-contents)

## Step 3. Create Entry Point and Queue

### 1. Create Entry Point in Management Portal 

- Click on **_Provisioning_** and select **_Entry Points/Queues_** > **_Entry Point_**.

- Click on `New Entry Point`.

- Input **_Name_** as `FBM_EP`.

- Select `Social Channel` in the **_Channel Type_** section.

- Select `Facebook Messenger` in the **_Social Channel Type_** section.
- 
- Leave the **_Asset Name_** as the configured value earlier.

- Set **_Service Level Threshold_** as `300` seconds.

- The **_Time Zone_** can stay as default value.

- Click on **Save** after comparing your values with the screenshot below.

  <img align="middle" src="images/Lab4_13.jpg" width="1000" />

### 2. Create Queue in Management Portal 

- Click on **_Provisioning_** and select **_Entry Points/Queues_** > **_Queue_**.

- Click on `New Queue`.

- Input **_Name_** as `FBM_Q`.
- 
- Select `Social Channel` in the **_Channel Type_** section.

- Click `Add Group` in the **_Conversation distribution_** section.

- Select the Agent based teams created in the previous lab and click `Save` . Once saved, click `Close` to exit this window. 

- Input **_Maximum Time in Queue_** as `300`.

- The **_Time Zone_** can stay as default value.

- Click on **Save** after comparing your values with the screenshot below.

  <img align="middle" src="images/Lab4_14.jpg" width="1000" />

[Back to top](#table-of-contents)

## Step 4. Create/Upload Facebook Messenger flow

### 1. Initial flow loading

- Download the default Facebook Inbound flow from the [GitHub page](https://github.com/CiscoDevNet/webexcc-digital-channels){:target="_blank"}.

- Navigate to **Webex Connect Flows** -> **v2.1** -> **Facebook Inbound Flow.workflow.zip**, select the zip file and click download.

- Unzip the downloaded file.

- Go to Webex Connect, click on **Services** and select the service in which the Asset is created in step 2. It should be **My First Service**

- In the service click on **FLOWS** -> **CREATE FLOW** .

<img align="middle" src="images/Lab3_19.jpg" width="1000" />

- Enter the **FLOW NAME** as **FBM Inbound Flow**, select the **TYPE** as **Work Flow** and under **METHOD** select **Upload a flow**.

- Drag and drop the **Facebook Inbound Flow.workflow** flow file that you unzipped, click **CREATE** and then click **SAVE**.

<img align="middle" src="images/Lab4_2.jpg" width="1000" />


### 2. Start node and Custom Variables

- A page will load with the imported workflow. We must make some changes to the default inbound flow based on our setup.
  
- First Click `Save` in the `Configure APP Event` page that loaded, this defines what will trigger the flow and the default settings are already good.

<img align="middle" src="images/Lab4_3.jpg" width="1000" />

- Click on the gear button on the top right to load the flow settings dialog

<img align="middle" src="images/Lab4_19.jpg" width="1000" />

- Select the Custom Variables tab and set the following Default Values:

*FBPageID*: to the numeric string in the m.me link we saved earlier in Step 2.
*appid*: Application ID (appID) from the FBM Asset from Step 2

<img align="middle" src="images/Lab4_17.jpg" width="1000" />

- Click `Save`

### 3. Edit Queue Task node

- In the created workflow find the **Queue Task**, click twice, select the **QUEUE NAME** as **FBM_Q** and add Skill requirement for Sales to be True and click on **SAVE**.

<img align="middle" src="images/Lab4_18.jpg" width="1000" />

- Finally click on Make Live on top right corner
  
<img align="middle" src="images/Lab4_20.jpg" width="1000" />

- Select the Application/Asset that we have created and click `Make Live`.

<img align="middle" src="images/Lab4_21.jpg" width="1000" />

- Wait for 2 minutes and verify that the flow is published successfully.

[Back to top](#table-of-contents)

## Step 5. Verification - start Facebook Chat and accept the request

- Open a new tab and login to the Agent Desktop if you haven't done already and make the agent Available (if you haven't done already in Lab2). 
  <img align="middle" src="images/Lab2_Agent1.png" width="1000" />

- Open a new tab on the same browser session to make sure you are still authenticated to Facebook. Go to the M.me URL you copied in Step 2 and the following FBM page should load with the Facebook Business page chat you created earlier

<img align="middle" src="images/Lab4_23.jpg" width="1000" />

- Start chatting and that should trigger a contact into Webex CC that will get routed according to the flow we configured in Step 4. A notification should appear that should help you switch to the agent desktop tab to accept the contact

<img align="middle" src="images/Lab4_24.jpg" width="1000" />
<img align="middle" src="images/Lab4_25.jpg" width="1000" />

- Type a response and hit send button.
  <img align="middle" src="images/Lab4_26.jpg" width="1000" />

- Response will be received in the other tab where the FBM page is:

<img align="middle" src="images/Lab4_27.jpg" width="1000" />

- End the contact
  <img align="middle" src="images/Lab4_28.jpg" width="1000" />

- Add wrap up and close the task. 
  <img align="middle" src="images/Lab4_29.jpg" width="1000" />


[Back to top](#table-of-contents)
---

### Congratulations, you have completed this section! 

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2013/Home.html";}
function nextLab() 
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2013/Lab5_SMS.html";
 }
</script>

<div id="button-row">
<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Home Page</button>

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go to the Next Lab</button>

</div>

