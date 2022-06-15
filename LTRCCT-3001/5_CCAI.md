---
title: 'Lab 5.1: CCAI Integration'
---

# Table of Contents
- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
    - [Lab Objective](#lab-objective)
    - [Pre-requisites](#pre-requisites)
    - [Quick Links](#quick-links)
- [Lab Section](#lab-section)
  - [Step 1. Create a gmail account (Optional)](#step-1-create-a-gmail-account-optional)
  - [Step 2: Create OAuth client ID and secret](#step-2-create-oauth-client-id-and-secret)
  - [Step 3. Authorize Google Dialog flow node in Webex Connect](#step-3-authorize-google-dialog-flow-node-in-webex-connect)
  - [Step 4. Enable Dialogflow and create agent](#step-4-enable-dialogflow-and-create-agent)
  - [Back to top](#back-to-top)
    - [Congratulations, you have completed this section!](#congratulations-you-have-completed-this-section)
  

# Introduction

### Lab Objective

In this Lab, we will go through the tasks that are required to complete the general pre-configuration of CCAI bot in Webex Connect. 

### Pre-requisites

- You have received the access credentials with a full admin access 

### Quick Links

> Control Hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="_blank"}**\
> Connect: https://cl2pod**X**.imiconnect.io/ (where **X** is your POD number)

# Lab Section

## Step 1. Create a gmail account (Optional) 

- We will need a Gmail accout to get started with this lab

- You can use your own personal Gmail account for this lab or create a free account by following the steps here: https://support.google.com/mail/answer/56256?hl=en 

## Step 2: Create OAuth client ID and secret

- Login to https://console.cloud.google.com/ using the Gmail account mentioned in Step-1. 

- Select **Country** , Accept the terms of service and Click **Agree and Continue**
<img align="middle" src="images/Lab5a_1.png" width="1000" />

- On the top left, click **Select a Project** and then **New Project**
<img align="middle" src="images/Lab5a_2.png" width="1000" />

- Enter a desired **Project Name** and click **Create**
<img align="middle" src="images/Lab5a_3.png" width="1000" />

- Once the project is created, under Notifications section, click **Select Project**
<img align="middle" src="images/Lab5a_4.png" width="1000" />

- Verify that the project created in the previous step is selected on the top left. 

- Navigate to **API and services** > **Credentials**
<img align="middle" src="images/Lab5a_5.png" width="1000" />

- Navigate to Credentials > Create Credentials > OAuth client ID
<img align="middle" src="images/Lab5a_6.png" width="1000" />

- Click **Configure Consent Screen**
<img align="middle" src="images/Lab5a_7.png" width="1000" />

- Select **User Type** as **External** and click **Create**
<img align="middle" src="images/Lab5a_8.png" width="1000" />

- Input a desired **App name** and select the **User supported email** (Enter the Gmail account mentioned in Step-1 )
<img align="middle" src="images/Lab5a_9.png" width="1000" />

- Input **Authorised domain** as **imiconnect.io**

- Input **Email addresses** as the Gmail account mentioned in Step-1. Click **Save and Continue**
<img align="middle" src="images/Lab5a_10.png" width="1000" />

- In the **Scopes** section, no configuration is required. Click **Save and Continue**
<img align="middle" src="images/Lab5a_11.png" width="1000" />

- In the **Test users** section, click **Add Users**
<img align="middle" src="images/Lab5a_12.png" width="1000" />

- Input email address in the add users section (Use the Gmail account mentioned in Step-1) and click **Add**
<img align="middle" src="images/Lab5a_13.png" width="1000" />

- Click **Save and Continue**
<img align="middle" src="images/Lab5a_14.png" width="1000" />

- Once the OAuth consent screen configurations are complete, click on **Credentials**
<img align="middle" src="images/Lab5a_15.png" width="1000" />

- Click **Create Credentials** > **OAuth client ID**
<img align="middle" src="images/Lab5a_16.png" width="1000" />

- Select **Application type** as **Web application** and a desired **Name**

- Click **Add URI** and input the value as **https://oauthus.imiconnect.io/callback** and click **Create**
<img align="middle" src="images/Lab5a_17.png" width="1000" />

- Copy the **Client ID** , **Client Secret** to a text editor in the local computer. Also, **Download JSON** .  We will need these values at a later stage to complete the configuration. 

- Click **OK**

<img align="middle" src="images/Lab5a_18.png" width="1000" />

## Step 3. Authorize Google Dialog flow node in Webex Connect 

- Login to your respective Webex Connect UI using the provided URL https://cl2pod**X**.imiconnect.io/ (where **X** is your POD number).

- Navigate to Assets > Integrations > Dialogflow ES > Manage 
<img align="middle" src="images/Lab5a_19.png" width="1000" />

- Click **Add Authorization**
<img align="middle" src="images/Lab5a_20.png" width="1000" />

- Input a desired **Authorization Name** . Input the **Client ID**, **Client Secret** value that was obtaines in Step-2. Click **Authorize**
<img align="middle" src="images/Lab5a_21.png" width="1000" />

- When redirected to google login, use the same credentials mentioned in Step-1. 
<img align="middle" src="images/Lab5a_22.png" width="1000" />

- After login, click **Continue**
<img align="middle" src="images/Lab5a_23.png" width="1000" />

- Click **Continue**
<img align="middle" src="images/Lab5a_24.png" width="1000" /> 

- Verify that the authorization is added successfully and marked as Default. 
<img align="middle" src="images/Lab5a_25.png" width="1000" />

## Step 4. Enable Dialogflow and create agent 

- Login to https://console.cloud.google.com/ using the Gmail account mentioned in Step-1. 

- In the search window, input **Dialogflow API** and click the **Dialogflow API** option under marketplace. 
<img align="middle" src="images/Lab5a_26.png" width="1000" />

- Click **Enable**
<img align="middle" src="images/Lab5a_27.png" width="1000" />

- Go to https://dialogflow.cloud.google.com and accept the **Terms of service** and click **Accept**
<img align="middle" src="images/Lab5a_28.png" width="1000" />

- Click **Create Agent**
<img align="middle" src="images/Lab5a_29.png" width="1000" />

- Input a desired **Agent name** , select the **Google project** that was created in Step-2. Click **Create**
<img align="middle" src="images/Lab5a_30.png" width="1000" />

- Click **Intents** and click **Create Intent**
<img align="middle" src="images/Lab5a_31.png" width="1000" />

- Input intent name as **Agent Handover** amd click **Add Training Phrases**
<img align="middle" src="images/Lab5a_32.png" width="1000" />

- Input some sample training phrases as shown in the image below and click **Add parameters and action**
<img align="middle" src="images/Lab5a_33.png" width="1000" />

- Input **LIVE_AGENT_HANDOVER** (this will be used later in the flow configuration) as the parameter name  click **Add Response**
<img align="middle" src="images/Lab5a_34.png" width="1000" />

- Input a desired response for this intent and click **Save**
<img align="middle" src="images/Lab5a_35.png" width="1000" />

[Back to top](#table-of-contents)
---

### Congratulations, you have completed this section! 

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/4_TaskBot.html";}
function nextLab() 
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/5.2_CCAIFlowConfig.html";
 }
</script>

<div id="button-row">
<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go To Previous Lab</button>

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go to the Next Lab</button>

</div>
