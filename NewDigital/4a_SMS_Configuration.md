---
title: 'Lab 4a: Asset creation end to end(SMS)'
---

<iframe width="1024" height="576" src="https://www.youtube.com/embed/luS7cmrB71Y" title="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents

- Lab 4a - Asset creation end to end (SMS)
    * SMS number procurement
    * Create SMS Asset and Register to WebexCC
    * Create EntryPoint and Queue
    

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

## Lab 4a - Asset creation end to end (SMS)

### 1. SMS number procurement
- SMS Numbers cannot be procured directly from the WxCC integrated IMI Connect tenant

- SMS Numbers are not assigned by default to any of the WxCC tenants.

- Please note that Partners have to go through a procurement process and work with your respective PSAM to enable SMS and get numbers assigned to the gold tenant

- Once the procurement process is completed, SMS Numbers are assigned to the tenant by the backend operations team

- Pleae complete this step before proceeding further.

### 2. Create SMS Asset and Register to WebexCC
- Customer admin logs in to IMI connect UI  (this is specific to the tenant you are using) and is provided agter tenant creation. 
    - Please contact your Cisco Partner Success Account Manager (PSAM) if there are any challenges identifying the IMI connect URL or login details

- Select Assets -> Numbers -> Select the number to configure (There will be 2 entries of the same number. Select the entry which has the WxCC icon and also has PCI tag)

- Go to Actions > Manage > Resister to Webex CC > In the resulting window select the service and click ‘Register’.

### 3. Create EntryPoint and Queue

- Log into Webex Contact Centre Administration portal URL with the admin credentials go to Menu > Provisioning > Entry Point/Queues > Entry Point

- Select `New Entry Point` and enter the respective values and click save.
  - Channel type should be selected as Social
- go to Menu > Provisioning > Entry Point/Queues > Queue

- Select `New Queue` and enter the respective values and click save.
  - Channel type should be selected as Social > SMS

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
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/NewDigital/4b_SMS_Configuration.html";
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
