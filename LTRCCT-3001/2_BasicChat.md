---
title: 'Lab 2: Chat Configuration'
---


# Table of Contents

- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
  - [Creating a Service](#creating-a-service)
  - [> 6. Click Create](#-6-click-create)
  - [Creating an App](#creating-an-app)
  - [Create a website](#create-a-website)
  - [Conecting to Webex Contact Center](#conecting-to-webex-contact-center)
    - [Congratulations, you have completed Lab2 tasks!](#congratulations-you-have-completed-lab2-tasks)


# Introduction

In this lab exercise we are going to configure a basic in Live Chat applet and deploy it on a website that you can access directly from the internet.  We will be downloading Workflow templates from GitHub, creating a free website on glitch.me, work with Webex Copnnect Flows and much more.

## Creating a Service

- Navigate to https://cl2podXX.imiconnect.io/ (where the XX is your lab ID)
- Click the **Create New Service** button
- Create a name for your service
- Navigate to [Workflow GitHub](https://github.com/CiscoDevNet/webexcc-digital-channels/tree/main/Webex%20Connect%20Flows)
- Download: [Live Chat Inbound](https://github.com/CiscoDevNet/webexcc-digital-channels/blob/main/Webex%20Connect%20Flows/v2.1/Live%20Chat%20Inbound%20Flow.workflow.zip)
- Unzip workflow file
- Click View My Flows 
- For each workflow file: 
> <img align="right" src="images/Lab2_Create_Workflow.PNG"  height="150"/>

> 1. Click Create Flow
> 2. Use the workflow file name for the Flow Name 
> 3. Type: Workflow 
> 4. Metod: Upload a flow 
> 5. Attach the unzipped workflow file 
> 6. Click Create
----


## Creating an App
- From the service:
  - Click configure Apps
  - Configure New App => Mobile Web
- Give your App a Name
- Enable Live Chat / In-App Messaging
  - Select Transport Protocals
  - Select "Use Secured Port"
  - Click Save
  - Click Register to Webex CC

## Create a website 
- In a new tab, go to [Glitch](glitch.com)
- Create a new account using the sign up button
  - Select Email Magic Link
  - Create a Hello World Website
    - Note the URL
- 

## Conecting to Webex Contact Center

- Log into Webex Contact Center as Admin
  - Create an Entry Point 
  - Create a Queue









---

[To top of this lab](#table-of-contents)



---

### Congratulations, you have completed Lab2 tasks! 

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/1_PreReq.html";}
function nextLab() 
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/3_QnABot.html";
 }
</script>

<div id="button-row">
<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go to the Previous Lab</button>

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go to the Next Lab</button>

</div>
