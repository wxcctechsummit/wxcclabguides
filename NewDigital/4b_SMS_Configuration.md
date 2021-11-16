---
title: 'Lab 4b: Workflow Association(SMS)'
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/pfE2fn4RoCc" title="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents

- Lab 4b - Workflow association (SMS)
    * Create/Upload SMS flow
    * Add Authorizations for each of the Engage and WxCC nodes
    * Demo     

# Introduction

## Lab Objective
This lab is designed to complete required SMS configurations in WxCC/IMI. You will be able to initiate a contact from mobile number (SMS) and will be able to accept and respond to the SMS contact by logging in as an agent.

We will be configuring  SMS Asset, Entry Point, Queue and corresponding workflows.

## Pre-requisite
- WxCC Portal, Agent Desktop and IMI connect URL.
- Admin credentials to complete configurations in WxCC portal and IMI connect.
- Agent Credentials to Handle the Chat
- SMS number procurement process should be completed (Please work with your PSAM)
- SMS number should be assigned in your IMI Conenct tenant

## Lab 4b - Workflow Association (SMS)

### 1. Create/Upload SMS flow

- Download the template flows from "https://github.com/CiscoDevNet/webexcc-digital-channels" link.

- Select the appropriate data center flows and select the zip file and click download.

- Unzip the downloaded file.

- In IMI connect click on Services and select the service in which the Asset is created.

- Navigate to Flows -> Create Flow -> Enter the flow name, select the type as work flow and under method select "upload a flow".

- Drag and drop the "SMS_Inbound_Message_US.workflow" flow that is downloaded in zip file and click create and then click save.

### 2. Add Authorizations for each of the Engage and WxCC nodes

- Double click on Engage and WxCC node and select the authorization if we already have one, else create a new one under Node Runtime Authorization.

- For Engage node authorization, provide the Authorization Name and client details that was shared by IMI Team upon tenant provisioning and click authorize.

- For WxCC node authorization, provide the Authorization Name and click authorize. This routes to the WxCC login page. Provide the Admin user email address and click sign in.
`NOTE: Repeat the step 10 for all Engage and WxCC nodes.`

-  After adding authorization details, click on save on top right corner.

-  Finally click on Make Live on top right corner -> Select the Application/Asset that we have created and click Make Live.

### 5. Demo

- Sent a SMS from your mobile phone of any text message application to the number configured in IMI conenct 

- Login to agent desktop

- Once the agent goes Available, the SMS contact will be offered to the agent. Click "Accept" to handle the FB messenger chat.

- Add a reply and hit send button 

- Add wrap up and close the task.

---

### Congratulations, you have completed this section! 
### We would like to keep track of your progress and make sure that we are giving you effective support. Please take approximately one minute to complete a short survey.

[Back to top](#table-of-contents)

---
Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial page created | Gagarin JS (gasathiy@cisco.com) | 09 Nov 2021 |
| 2.0 | SMS content update | Abhishek Singh (asingh9@cisco.com) | 15 Nov 2021 |
| 3.0 | Format Changes | Gagarin JS (gasathiy@cisco.com) | 16 Nov 2021 |
| 4.0 | Video guide addition | Gagarin JS (gasathiy@cisco.com) | 16 Nov 2021 |

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/NewDigital/HomePage.html";}
function nextLab() 
 {
 window.open("https://app.smartsheet.com/b/form/ff1e015c4aed46bfab3f5caed7850aa4", '_blank');
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/NewDigital/5_Templates_Bots.html";
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
  padding: 10px;">Take Survey and Go to Next Lab</button>


</div>
