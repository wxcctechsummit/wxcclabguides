---
title: 'Lab 5: SMS Configuration'
---

# Table of Contents
- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
    - [Lab Objective](#lab-objective)
    - [Pre-requisite](#pre-requisite)
- [Lab Section](#lab-section)
    - [Configuration Order](#configuration-order)
  - [Step 1. Verify SMS Number Assignment](#step-1-verify-sms-number-assignment)
  - [Step 2. Create SMS Asset and Register to WebeXCC](#step-2-create-sms-asset-and-register-to-webexcc)
    - [1. Create Email Assest](#1-create-email-assest)
  - [Step 3. SMS Entry Point and Queue creation](#step-3-sms-entry-point-and-queue-creation)
    - [1. Create Entry Point in Managment Portal](#1-create-entry-point-in-managment-portal)
  - [Step 4. Create/Upload SMS flow](#step-4-createupload-sms-flow)
  - [Verification - send SMS and accept the request](#verification---send-sms-and-accept-the-request)
  - [Back to top](#back-to-top)
    - [Congratulations, you have completed this section!](#congratulations-you-have-completed-this-section)


# Introduction

### Lab Objective

In this Lab, we will go through the tasks that are required to complete the basic SMS integration. You will be able to initiate a SMS contact to the Contact Center and be able to accept/respond to the contact by logging in as an agent.  

In this lab you will be configuring **SMS** number settings, SMS Assets, Entry Point and corresponding workflows. All these steps are required for integrating SMS with our application.  


### Pre-requisite

1. You recived an admin credentials to configure in Managment Portal and Webex Connect.
2. You recived the SMS number associated with your tenat.
3. You have successfully completed the previous Lab **Preconfiguration**

# Lab Section

### Configuration Order
<img align="middle" src="images/Lab2_ConfigOrder.png" width="1000" />


## Step 1. Verify SMS Number Assignment

>**Note**: For this lab, we created a Gmail account. Optionally, use your own account for polling and handling the emails. It can be a Gmail account or Office 365 account or any account which has email forwarding.




## Step 2. Create SMS Asset and Register to WebeXCC

### 1. Create Email Assest

- As an admin, login to Webex Connect UI using the provided URL https://cl1pod**X**.imiconnect.io/ (where **X** is your POD number).

- Select **Assets** -> **Apps** -> **CONFIGURE NEW APP** -> **Email**.

<img align="middle" src="images/Lab2_Assest1.png" width="1000" />



## Step 3. SMS Entry Point and Queue creation

### 1. Create Entry Point in Managment Portal 

- Click on **_Provisioning_** and select **_Entry Points/Queues_** > **_Entry Point_**.

- Click on `New Entry Point`.

- Input **_Name_** as `Email_EP`.

- Select `Email` in the **_Channel Type_** section.

- Leave the **_Asset Name_** as appered value `EmailASSET`.

- Set **_Service Level Threshold_** as `2` hours.

- The **_Time Zone_** can stay as default value.

- Click on **Save** after comparing your values with the screenshot below.

<img align="middle" src="images/Lab2_Email_EP.png" width="1000" />



## Step 4. Create/Upload SMS flow

- Download the email flow from the [GitHub page](https://github.com/CiscoDevNet/webexcc-digital-channels){:target="_blank"}.

- Navigate to **Webex Connect Flows** -> **v2.1** -> **Email Inbound Flow.workflow.zip**, select the zip file and click download.

- Unzip the downloaded file.

- Go to Webex Connect, click on **Services** and select the service in which the Asset is created in step 2. It should be **My First Service**

- In the service click on **FLOWS** -> **CREATE FLOW** 

- Enter the **FLOW NAME** as **Email Inbound Flow**, select the **TYPE** as **Work Flow** and under **METHOD** select **Upload a flow**.

- Drag and drop the **Email Inbound Flow.workflow** flow that is downloaded in zip file, click **CREATE** and then click **SAVE**.

<img align="middle" src="images/Lab2_WF1.png" width="1000" />










[To top of this lab](#table-of-contents)

## Verification - send SMS and accept the request

- Go to the Gmail account and send an email to the support email address that was initially configured in the Email Asset creation.

- Go to the Agent Desktop and make the agent Available. 

<img align="middle" src="images/Lab2_Agent1.png" width="1000" />

- The Email will be offered to the agent. Click "Accept" to handle the email.

<img align="middle" src="images/Lab2_Agent2.png" width="1000" />

- Click "Reply" or Reply All" to reply to the email and enter the body of the email and hit send button.

- Add wrap up and close the task.


[Back to top](#table-of-contents)
---

### Congratulations, you have completed this section! 

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2013/Home.html";}
function nextLab() 
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2013/Lab3_Chat.html";
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

