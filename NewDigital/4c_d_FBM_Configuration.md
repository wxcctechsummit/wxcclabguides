---
title: 'Lab 4(c,d): Facebook Configuration'
---

<iframe width="1024" height="576" src="https://www.youtube.com/embed/Di-cmQhrnts" title="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents

- Lab 4c - Asset creation end to end 
    * Facebook page configuration
    * Create Facebook Asset and Register to WebeXCC
    * Create EntryPoint and Queue
    
- Lab 4d - Workflow association
    * Create/Upload Facebook flow
    * Add Authorizations for each of the Engage and WxCC nodes
    * Demo 

# Introduction

## Lab Objective
This lab is designed to complete required Facebook configurations in WxCC/IMI. You will be able to initiate a contact from Facebook messenger and will be able to accept and respond to the Facebook contact by logging in as an agent.

We will be configuring  Facebook Asset, Entry Point, Queue and corresponding workflows.

## Pre-requisite
- WxCC Portal, Agent Desktop and IMI connect URL.
- Admin credentials to complete configurations in WxCC portal and IMI connect.
- Agent Credentials to Handle the Chat
- Facebook business page 

## Lab 4c - Asset creation end to end

### 1. Facebook page configuration
- Customer/Partner should have a Facebook account 

- Login to Facebook and create a business page that can be used in WxCC for polling and handling the messenger chats

- Additional details of facebook page setup is available here: https://www.facebook.com/business/pages/set-up

### 2. Create Facebook Asset and Register to WebeXCC
- Customer admin logs in to IMI connect UI  (this is specific to the tenant you are using) and is provided agter tenant creation. 
    - Please contact your Cisco Partner Success Account Manager (PSAM) if there are any challenges identifying the IMI connect URL or login details

- Select Assets -> Apps -> Configure New App -> Messenger -> Click on add messenger page

- Authenticate with your FB account where you have a page already created -> Select the respective page that you want to integrate -> Provide the name and click ‘Save’

-  Click ‘Register to Webex CC’  in the ‘Configure New App-Messenger’ window ->  In the resulting window select the service and click ‘Register’.

### 3. Create EntryPoint and Queue

- Customer admin logs into “CJP Management Portal” URL with the credentials and accesses the menu ‘Provisioning -> Entry Point/Queues -> Entry Point’.

- Select “New Entry Point” and enter the respective values and click save.

- Customer admin accesses the menu ‘Provisioning -> Entry Point/Queues -> Queue’ • Select “New Queue” and enter the respective values and click save.

## Lab 4c - Asset creation end to end

### 4. Create/Upload Facebook flow

- Download the template flows from "https://github.com/CiscoDevNet/webexcc-digital-channels" link.

- Select the appropriate data center flows and select the zip file and click download.

- Unzip the downloaded file.

- In IMI connect click on Services and select the service in which the Asset is created.

- Navigate to Flows -> Create Flow -> Enter the flow name, select the type as work flow and under method select "upload a flow".

- Drag and drop the "FBM_Inbound_Message_US.workflow" flow that is downloaded in zip file and click create and then click save.

### 5. Add Authorizations for each of the Engage and WxCC nodes

- Double click on Engage and WxCC node and select the authorization if we already have one, else create a new one under Node Runtime Authorization.

- For Engage node authorization, provide the Authorization Name and client details that was shared by IMI Team upon tenant provisioning and click authorize.

- For WxCC node authorization, provide the Authorization Name and click authorize. This routes to the WxCC login page. Provide the Admin user email address and click sign in.
`NOTE: Repeat the step 10 for all Engage and WxCC nodes.`

-  After adding authorization details, click on save on top right corner.

- Click on settings on top right corner and click Custom variables. Here in bizemailid row, update the details of the facebook asset that was added and click save.

-  Finally click on Make Live on top right corner -> Select the Application/Asset that we have created and click Make Live.

### 5. Demo

-  Access the Facebook business page that was integrated with Webex CC

- Access the messenger section and send a new message

- Login to agent desktop

- Once the agent goes Available, the FB messenger chat will be offered to the agent. • Click "Accept" to handle the FB messenger chat.

- Add a reply and hit send button 

- Add wrap up and close the task.

---

### Congratulations, you have compleated this section! 
### We would like to keep track of your progress and make sure that we are giving you effective support. Please take approximately one minute to complete the short survey.

[Back to top](#table-of-contents)

---

Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Abhishek Singh (asingh9@cisco.com) | 08 Nov 2021 |
| 2.0 | Format Changes | Gagarin JS (gasathiy@cisco.com) | 09 Nov 2021 |


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