---
title: 'Lab 2: Chat Configuration'
---


# Table of Contents

- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
  - [Creating a Service](#creating-a-service)
  - [Creating an App](#creating-an-app)
  - [Create a Chat Template](#create-a-chat-template)
  - [Create a Website](#create-a-website)
  - [Conecting to Webex Contact Center](#conecting-to-webex-contact-center)
  - [Launch the Engage Portal](#launch-the-engage-portal)
  - [Adding the Applet to Your Website](#adding-the-applet-to-your-website)
  - [Modifying the Chat Flow](#modifying-the-chat-flow)
  - [Time to test our first chat flow!](#time-to-test-our-first-chat-flow)
    - [Congratulations, you have completed Lab2 tasks!](#congratulations-you-have-completed-lab2-tasks)


# Introduction

In this lab exercise we are going to configure a basic in Live Chat applet and deploy it on a website that you can access directly from the internet.  We will be downloading Workflow templates from GitHub, creating a free website on glitch.me, work with Webex Copnnect Flows and much more.

---

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
> 
> ---

[To top of this lab](#table-of-contents)
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

  ---

[To top of this lab](#table-of-contents)
## Create a Chat Template
- Click the Wrench for the Tools menu <img src="images\Lab2_Tools.PNG" Height="20">
- Click Templates <img src="images\Lab2_Templates.PNG" height="20">
- Click Add New Template
> Name: Give your template a meaningful name 
> 
> Channel: Live Chat / In-App Mesaging
> 
> Message Type: Form
>
>Title: Please provide the following information.
>
>Form Fields:
>
>> Click Add Field
>>
>> Type: Name
>>
>> Name: Name
>>
>> Label: Name
>>
>> Mandatory Field: Enabled
> 
> Create another form field for Email Address
 
---


[To top of this lab](#table-of-contents)
## Create a Website 
- In a new tab, go to [Glitch](https://glitch.com)
- Create a new account using the sign up button
  - Select Email Magic Link
  - Create a Hello World Website
    - Note the URL 
  
[To top of this lab](#table-of-contents)
## Conecting to Webex Contact Center

- Log into Webex Contact Center as Admin
  - Create an Entry Point:
    > Name: Name of your choice 
    >
    > Channel Type: Chat 
    >
    > Asset Name: Your Asset
    >
    > Servie Level: 120

    ---
  - Create a Queue
    > Name: Name of your choice 
    >
    > Channel Type: Chat 
    >
    > Queue Routing Type: Longest Available agent
    >
    >Chat Distribution: Put your team into Group 1
    >
    > Servie Level Threshold: 120
    >
    > Maximum Time in Queue: 3600

    ---

[To top of this lab](#table-of-contents)

## Launch the Engage Portal

- Click on **New Digital Channels** to launch the Engage Portal <img align="" src="images\Lab2_New_Digital_Channels.PNG" height="20">
  - Click on Assets <img align="" src="images\Lab2_Assets.PNG" height="25">
    - You will see A live Chat Channel type With the name os your asset
    - Click edit in the Action column
    - Click Websites
      - Click Add Website 
        > Display Name: North Pole Holiday Infused Widgets and Bobbles
        >
        > Domain: the domain of your glitch website
        > 
        > Save Changes! 
        >
        > Click the Website Settings Banner back option <img src="images\Lab2_WS_Settings_Back.PNG" height="15">
        >
        > Click on the Installation Tab
        >
        > Copy out the Code
        >
        ---

[To top of this lab](#table-of-contents)

## Adding the Applet to Your Website
- Return to the Glitch tab in youe browser
- Open index.html
- Scroll to the bottom of the code
- Paste the applet code between the body and html closing tags
- Click the preview button (note that chat will not work yet as we need to setup the flow first)

[To top of this lab](#table-of-contents)

## Modifying the Chat Flow
- Go back to the service that you created
- Click on flows
- Click on the name of the flow
- In the upper right corner click the settings cog <img src="images\Lab2_Settings _Cog.PNG" height="20">
  > Click Custom Variables
  > 
  > Change Live Chat Domain to your Glitch domain
  > 
  > Change the appid to your appid
  > 
  > Click Save

  ---
- Double click on the Pre-chat Form node
  > Select the Form Template From the Dropdown 
  >
  > Click Save

  ---
- Double click on the Recieve node
  > Select the Form Template From the Dropdown 
  >
  > Click Save
  
- DoubleClick the Queue Task node
  > Select the queue that you created in the Queue name drop down

  ---
- Click Save
- Click Make Live
  
  ---

[To top of this lab](#table-of-contents)
## Time to test our first chat flow!
- Log into the contact center as an agent
- open the chat applet on your website and start a chat

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
