---
title: 'Lab 3(a,b): Chat Configuration'
---

<iframe width="1024" height="576" src="https://www.youtube.com/embed/sWkg876L67A" title="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents

- Lab 3a - Asset creation end to end (Chat)
    * Service configuration
    * Create Chat Asset and Register to WebeXCC
    * Create EP/Q
    * Template configuration 
    * Website configuration

- Lab 3b - Workflow association(Chat)
    * Create/Upload Chat flow
    * Add Authorizations for each of the Engage and WxCC nodes
    * Demo 


# Introduction

## Lab Objective
This lab is designed to complete required Chat configurations in WxCC/IMI. You will be able to initiate a Chat and will be able to accept and respond to the Chat by logging in as an agent.

We will be configuring  Service, Chat Assets, Entry Point, Queue, Chat Template, Website Settings, and corresponding workflows.

## Pre-requisite
- WxCC Portal, Agent Desktop and IMI connect URL.
- Admin credentials to complete configurations in WxCC portal and IMI connect.
- Agent Credentials to Handle the Chat.

## Lab 3a - Asset creation end to end (Chat)
### 1. Service Creation
- Customer admin logs in to IMI connect UI using the URL provided by the IMI team with the credentials. Here for the demo tenant the URL is "https://solutionassuranceesrgt-sa.imiconnect.io/login". 

- Login to IMI connect, from menu goto Services=> CREATE NEW SERVICE

- Provide a Name

### 2. Chat Asset configuration and Register to Webex CC in IMI Connect
 
- Customer admin logs in to IMI connect UI using the URL provided by the IMI team with the credentials. Here for the demo tenant the URL is "https://solutionassuranceesrgt-sa.imiconnect.io/login". 

- Login to IMI connect, from menu goto Assets=> Apps => CONFIGURE NEW APP => Mobile / Web

- Provide a Name

- Toggle/Enable "Live Chat / In-AppMessaging" to "ON" and choose "PRIMARY TRANSPORT PROTOCOL as  MQTT" & "SECONDARY TRANSPORT PROTOCOL as Web Socket" and enable "Use Secured Port" and SAVE.

- Select "REGISTER TO WEBEX CC" and choose the Service you have created and REGISTER

### 3. Entry Point creation

- Customer admin logs into “WxCC Management Portal” URL with the credentials and access the menu ‘Provisioning -> Entry Point/Queues -> Entry Point’.

- Select “New Entry Point” and enter the respective values and click save

### 4. Queue creation

- Customer admin access the menu ‘Provisioning -> Entry Point/Queues -> Queue’.

- Select “New Queue” and enter the respective values and click save.


### 5. Chat Template Creation

- Login to IMI connect, goto TOOLS=> Templates=> ADD NEW TEMPLATE

- Provide a Name and choose CHANNEL as "Live Chat / In-APP Messaging"

- MESSAGE TYPE as "Form".

- Provide the TITLE "Welcome to WxCC IMI Chat Demo" as per your business requirement and this will be the welcome message.

- Add few fields which ever are required as per your business requirement.

- SAVE


### 6.Website Settings Configuration in IMI Engage

- Login to WxCC Management Portal access the menu and cross launch Engage Portal by choosing "New Digital Channels"

- Goto Assets => search and edit the chat asset which you have created in IMI connect

- Scroll down and choose "SAVE CHANGES"

- Scroll to top of the page and choose "Websites"

- Select "ADD WEBSITE"

- Enter the respective fields as per your business requirement

- Launch glitch.com, signup and choose New Project => glitch-hello-website

- Choose Change URL and copy the website url.

- Paste this in Domain field and SAVE CHANGES

- Scroll up, select "Appearance" and change the settings (Widget Color, Logo, Emojis, attachments etc.;) as per your requirement and SAVE CHANGES

- Scroll up, select "Widget Visibility" enable "Show the widget with a OOO Banner" and provide the required message "Our business hours are 9AM - 5PM" (This is Not a Mandatory field/step) and SAVE CHANGES

- Now go-back to edit your chat asset, select Installation and Copy the chat script.

- go-back to your project in glitch.com => index.html => paste the chat script between `</footer> and </body>`
 
## Lab 3b - Workflow association(Chat)

### 7. Create/Upload Chat flow

- Download the template flows from "https://github.com/CiscoDevNet/webexcc-digital-channels" link.

- Select the appropriate data center flows and select the zip file and click download.

- Unzip the downloaded file.

- In IMI connect click on Services and select the service in which the Asset is created in step 1

- Navigate to Flows -> Create Flow -> Enter the flow name, select the type as work flow and under method select "upload a flow".

- Drag and drop the "Livechat_Inbound_Message_US.workflow" flow that is downloaded in zip file and click create and then click save.

- Add Authorizations for each of the Engage and WxCC nodes

- Double click on Engage or WxCC node and select the authorization if we already have one, else create a new one under Node Runtime Authorization.

- For Engage node authorization, provide the Authorization Name and client details that was shared by IMI Team upon tenant provisioning and click authorize.

- For WxCC node authorization, provide the Authorization Name and click authorize. This routes to the WxCC login page. Provide the Admin user email address and click sign in.

`NOTE: Repeat this step for all Engage and WxCC nodes.`

- In the Create Conversation node, the website URL needs to be updated.

- In the in-app messaging node the chat template needs to be selected.

- In the receive node also, the chat template needs to be selected.

- In Queue task node, update authorization, media type, media channel and choose the appropriate queue name which we have created in WxCC Portal.

- After adding authorization details, click on save on top right corner.

- Click on settings on top right corner and select Custom variables. Here in appid row, update the appid of the Chat Asset which was initially created during "Chat Asset Creation" module and click save.

- Finally click on Make Live on top right corner -> Select the Application/Asset that we have created and click Make Live.


### 8. Initiate Chat as Customer

- Initiate Chat as customer from the website (glitch-hello-website url in our Demo) by providing the required details


### 9.Agent Desktop – Chat offering to an Agent, Acceptance, respond and closure

- Once the agent goes Available, the Chat will be offered to the agent. 

- "Accept" to handle the chat and respond to customer queries. 


---

### Congratulations, you have compleated this section! 
### We would like to keep track of your progress and make sure that we are giving you effective support. Please take approximately one minute to complete the short survey.

[Back to top](#table-of-contents)

---

Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Avinash Satrasala (avsatras@cisco.com) | 04 Nov 2021 |
| 2.0 | Format Changes | Gagarin JS (gasathiy@cisco.com) | 06 Nov 2021 |

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/NewDigital/HomePage.html";}
function nextLab() 
 {
 window.open("https://app.smartsheet.com/b/form/ff1e015c4aed46bfab3f5caed7850aa4", '_blank');
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/NewDigital/3c_d_Email_Configuration.html";
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
