---
title: "Lab 4: Email and Chat Configuration"
---

# Table of Contents

- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
  - [Lab Objective](#lab-objective)
  - [Pre-requisites](#pre-requisites)
  - [Quick Links](#quick-links)
- [Part 1: Email Configuration](#part-1-email-configuration)
  - [1. Setup test email account (Gmail example)](#1-setup-test-email-account-gmail-example)
  - [2. Email Entry Point, Queue and Routing Strategy](#2-email-entry-point-queue-and-routing-strategy)
    - [2.1 Email Entry point](#21-email-entry-point)
    - [2.2 Email Queue](#22-email-queue)
    - [2.3 Email Entry point routing strategy](#23-email-entry-point-routing-strategy)
  - [3. Email Template](#3-email-template)
  - [4. Test Email customer and agent experience](#4-test-email-customer-and-agent-experience)
- [Part 2: Chat Configuration](#part-2-chat-configuration)
  - [1. Chat Entry Point, Queue, Template and Routing Strategy](#1-chat-entry-point-queue-template-and-routing-strategy)
    - [1.1 Chat Entry Point](#11-chat-entry-point)
    - [1.2 Chat Queue](#12-chat-queue)
    - [1.3 Chat template](#13-chat-template)
    - [1.4 Chat Entry point routing strategy creation](#14-chat-entry-point-routing-strategy-creation)
  - [2. Predefined Chat Responses](#2-predefined-chat-responses)
  - [3. Test Chat customer and agent experience](#3-test-chat-customer-and-agent-experience)


# Introduction

## Lab Objectives

In this lab we will complete all configuration required to route emails and chats into WxCC.
You will be able to send an email to the Contact Centre and be able to accept/respond to the email by logging in as an agent.  
You will also have the ability to start a chat session with an agent from an embedded chat bubble on a website

## Pre-requisites

1. An Email account to be used in WxCC. It may be required to create an email in gMail or Office 365 for your Gold Tenant.
2. Portal and Agent Desktop URLs and credentials.
3. Lab 1 to 3 must be completed before starting Lab 4 as configuration done on previous labs is expected to be completed.

## Quick Links

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="_blank"}**\
> Gmail: **[https://mail.google.com/](https://mail.google.com/){:target="_blank"}**\
> w3schools JS Tryit Editor: **[https://www.w3schools.com](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_basic){:target="_blank"}**

# Lab 4 Part 1: Email Configuration

In this part, we will be configuring Email Account settings to ensure WxCC can fetch emails correctly. Then we will complete all required WxCC Portal configurations, Entry Point, Queue, corresponding Routing strategies, Routing rules and Email Template so that emails can be routed to an Agent.

## 1. Setup test email account (Gmail example)

> A GMAIL account is provided for this lab purpose please check the POD information that has been shared with you. Please reach out to your lab proctors if you have any issues.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/3JW039i7o18?rel=0" title="WxCC Lab #4: Setup test email account" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br>

Follow the instructions below to set the necesary settings on the GMAIL account:

- Open a new browser tab and login to your Gmail account. 

- Click on settings icon on top right corner -> Select `See all settings`.

- Click on `Forwarding and POP/IMAP` and enable  `POP Download` and `IMAP access`.

- Click on `Google Apps` icon on top right corner -> Select `Account`.

- Select `Security` option and turn `ON` the `Less secure app access`.

- Use this [link](https://accounts.google.com/b/0/DisplayUnlockCaptcha){:target="_blank"} to disable captcha for the account and click Continue.

## 2. Email Entry Point, Queue and Routing Strategy

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/RXCIflSXcE0?rel=0" title="WxCC Lab #4: EP Q RS" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 2.1 Email Entry point

- Login to [WxCC Portal](https://portal.wxcc-us1.cisco.com){:target="_blank"} and go to `Provisioning -> Entry Point/Queues -> Entry Point`.

- Click `New Entry Point` and enter the respective values and click save.

Configuration field | Suggested Value
--- | ---
Name | `EP_email_<ID>`
Channel Type | `Email`
Service Level Threshold | `24 hours`
Time Zone | `Default`

### 2.2 Email Queue

- Access the menu `Provisioning -> Entry Point/Queues -> Queue`.

- Click `New Queue` and enter the respective values.

Configuration field | Suggested Value
--- | ---
Name | `Q_email_<ID>`
Channel Type | `Email`
Service Level Threshold | `1 hours`
Maximum time in Queue | `24 hours`
Time Zone | `Default`

- Click `Add Group` in **Email Distribution** and select the team intended for email distrubution.  This should have been created earlier.

### 2.3 Email Entry point routing strategy

- Click `Routing Strategy` menu item which cross launches the routing strategy configuration webpage.

- Select the `EP_email_<ID>` created earlier click on `New Strategy` button.

- Enter the `Suggested` Routing strategy name `RS-EP_email_<ID>`.

- Proceed to configure the account connection setting by clicking `Add Email Account`.

- Configure the assigned GMAIL email account settings as below and **_Save_**.

Configuration field | Suggested Value
--- | ---
Email Address | GMAIL example 
Incoming Protocol | `IMAP`
Incoming Host | `imap.gmail.com`
Inbound Encryption | `SSL`
Inbound Port Number | `993`
SMTP Server | `smtp.gmail.com`
Outbound Encryption | `SSL`
Outbound Port Number | `465`
Username | GMAIL email address 
Password | GMAIL password 
Maximum Attachment size | `25 MB`
Attachment Limit | `3`
Mail Delay | `60 Seconds`
Maximum Messages/Cycle | `10`

- Click on `Add Routing Rule` and enter your routing rules and **_Save_**. The content in the subject line helps in subject line-based routing. A combination of ‘And’ and ‘Or’ rules can be applied. However, both ‘And’ and ‘Or’ can’t be added to the same rule.

Configuration field | Suggested Value
--- | ---
Routing Rule Name | `Sales Email Routing`
IF Email Subject Contains | `Sales`
THEN Queue To | `Q_email_<ID>`

- Finally select the queue from the drop-down list for the default routing as `Q_email_<ID>` and click Save.

## 3. Email Template

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/4RfDVQuJVZ8?rel=0" title="WxCC Lab #4: Predefined Email" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br>

- Back in the Routing strategy list view, click the `Resources` menu at the top and then choose `Predefined Emails`.

- Click on the `New` button.

- Use the insert macro’s option to add the customer name and agent name and their defaults. Also add text as appropriate to the template and save. The template will now be available to all agents to use.

Example:
```
Hello ${CustomerName},

<Required Information>

Regards,

${AgentName}
```

> **Note:** A Predefined Email provides agents with an email outline that can be modified or sent directly to customers. There is currently a limit of one Predefined Email per organization. If its status is set to Active, the Predefined Email will automatically appear in all new agent emails. 

## 4. Test Email customer and agent experience

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/_-nOekJs_6E?rel=0" title="WxCC Lab #4: Test Email" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br>



- Send test email from your personal or work email account to the configured email with the subject of `Sales`

- You can verify that email reaches GMAIL account by checking the previously open tab.

- If you haven't done so, login to [WxCC agent desktop](https://desktop.wxcc-us1.cisco.com){:target="_blank"} as Agent 1.

- Once the agent goes Available, the Email will be offered to the agent.

- Click `Accept` to handle the email.

- Click `Reply` or `Reply All` to reply to the email and enter the body of the email and hit send button. This will also show the predefined email template prefilled in the message body.

- Add wrap up code and close the task.

# Part 2: Chat Configuration

Chat configuration is divided between to configuration interfaces:

- Webex Control Hub contains configuraiton for the Chat Template look and feel and schedule. It also contains configuration so you can plug a Virtual Agent to your chat but this configuration is outside the scope of this lab.

- WxCC Portal allows you to configure Chat Entry Point and Routing Strategy and the Queue which will distribute Chats to your agents.

## 1. Chat Entry Point, Queue, Template and Routing Strategy

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/QR8vilhQ2dA?rel=0" title="WxCC Lab #4: Chat EP Q Template and RS" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 1.1 Chat Entry Point
- Login to [WxCC Portal](https://portal.wxcc-us1.cisco.com){:target="_blank"} and go to `Provisioning -> Entry Point/Queues -> Entry Point`.

- Click `New Entry Point` and enter the respective values and click **_Save_**.

Configuration field | Suggested Value
--- | ---
Name | `EP_chat_<ID>`
Channel Type | `Chat`
Service Level Threshold | `60 seconds`
Time Zone | `Default`


### 1.2 Chat Queue

- Access the menu `Provisioning` -> `Entry Point/Queues` -> `Queue`.

- Click `New Queue` and enter the respective values.

Configuration field | Suggested Value
--- | ---
Name | `Q_chat_<ID>`
Channel Type | `Chat`
Service Level Threshold | `60 seconds`
Maximum time in Queue | `1800 seconds`
Time Zone | `Default`

- Click `Add Group` in **Chat Distribution** and select the earlier created team who is fielding chat requests

### 1.3 Chat template

- Switch web interface to [Webex Control Hub](https://admin.cisco.com){:target="_blank"}.

- From the left side menu click `Contact Center` and make sure the `Features` tab loads.

- Click `New` -> `Chat Template` and enter the respective values.

Configuration field | Suggested Value
--- | ---
Provide a unique name for your chat template | `ChatTemplate_<ID>`
Choose a preconfigured entry point | `EP_chat_<ID>`
Proactive Prompt | `Disabled`
Off-Hours | `Enabled`
Virtual agent | `Disabled`
Feedback | `Enabled`

- Click `Next` to configure the Off-Hours for this Chat template, what message will be shown to customers during off-hours and what are the Business Hours associated to this Chat Entry Point and Template. Feel free to adjust the settings according to your liking.

Configuration field | Suggested Value
--- | ---
Message| `We are currently offline. Please try again during our business hours.`
Business Hours| `Monday-Friday 24 hours, Timezone America/New_York`
Timezone | `United States: America/New York`

- Click `Next` and configure the look and feel of the chat template entry form. This will be what customers have to fill in to start a chat. Explore the different Attributes by clicking on them. **Name**, **Email**, **'How may I assist you?'** and **'Additional details'**. The only one you must edit in this Lab exercise is `How may I assist you?`, click on it and fill in the following field:

Configuration field | Suggested Value
--- | ---
Add category Options | `Sales` (Press Enter key)

- Click `Next` to show the **Branding and Identity** options and **Status Messages** which can be edited to meet the look and feel you are looking for in your template.

- Click `Next` to move to the next screen where you can customise the text for your chat template Feedback form.

- Click `Next` and then `Finish` to complete the chat template creation.

- Click `Download Embed Code` option to save the Chat_Code_Snippet text file. The code in that text file can be embedded into your website or used in any web based HTML+Javascript editor like the one found [here](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_basic){:target="_blank"}.


### 1.4 Chat Entry point routing strategy creation

- Go back to [WxCC Portal](https://portal.wxcc-us1.cisco.com){:target="_blank"} and click `Routing Strategy` menu item which cross launches the routing strategy configuration webpage.

- Select the `EP_chat_<ID>` created earlier click on `New Strategy` button.

- You will notice that Chat template field will be pre-populated with the chat template we configured and the Schedule we assigned.

- Enter the Routing strategy name as `RS-EP_chat_<ID>`.

- In **Chat Reason Mappings** select `Q_chat_<ID>` as the queue assined to the `Sales` category we created in previous step.

- Click **Apply** and then Click **_Save_**.


## 2. Predefined Chat Responses

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/lZT3ZzrIR0w?rel=0" title="WxCC Lab #4: Predefined Chat Responses" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br>

- Back in the Routing strategy list view, click the `Resources` menu at the top and then choose `Predefined Chat Responses`.

- Click on the `New` button and enter the respective values and click **_Save_**.

Configuration field | Suggested Value
--- | ---
Response Name | `PredefinedResponse_<ID>`
Status | `On`
Language | `English`
Queue | `All`
Content| `Hi, how can I help you today?`

> Optionally, add more predefined chat responses for a more realistic scenario when testing

## 3. Test Chat customer and agent experience

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/9MTtvkzi8jY?rel=0" title="WxCC Lab #4: Test Chat" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br>

- Navigate to a HTML+Javascript online editor like [this](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_basic){:target="_blank"}.

- Copy the code in Chat_Code_Snippet text file downloaded earlier and paste it after the `<body>` html tag. You should have the following on the left side of the editor (if using w3schools one).
  
```html
<!DOCTYPE html>
<html>
<body>
<script>
    //Name of the Customer Support Template: ChatTemplate_<ID>
    //Name of the Organisation: <POD Name>
      (function(document, script) {
      var bubbleScript = document.createElement(script);
      e = document.getElementsByTagName(script)[0];
      bubbleScript.async = true;
      bubbleScript.CiscoAppId =  'cisco-chat-bubble-app';
      bubbleScript.appPrefix = '';
      bubbleScript.DC = 'produs1.ciscoccservice.com';
      bubbleScript.orgId = '<your org ID>';
      bubbleScript.templateId = '<your template ID>';
      bubbleScript.src = 'https://bubble.produs1.ciscoccservice.com/bubble.js';
      bubbleScript.type = 'text/javascript';
      bubbleScript.setAttribute('charset', 'utf-8');
      e.parentNode.insertBefore(bubbleScript, e);
      })(document, 'script');
    </script>
The content of the body element is displayed in your browser.
</body>
</html>
```
- Click on the **Run** button, a Chat bubble button should appear at the bottom right of the browser window.

- Fill in the Chat form.

- If you haven't done so, login to [WxCC agent desktop](https://desktop.wxcc-us1.cisco.com){:target="_blank"} as Agent 1.

- Once the agent goes Available, the Chat will be offered to the agent.

- Click `Accept` to handle the Chat.

- Test the Predefined Chat Response functionality (click on the little chat bubble right above the response area in the Agent Desktop) and sending messages and attachments. `Complete` the chat when done.

### Congratulations, you are now ready to start Lab 5!

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/TechSummitRoW_2021/HomePage.html";}
function nextLab() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/TechSummitRoW_2021/Lab5.html";}
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
  padding: 10px;">Next Lab 5: Analyzer</button>

</div>
