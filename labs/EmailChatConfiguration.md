---
title: "Lab 5: Email and Chat Configuration"
---

# Table of Contents

- [Part 1: Email Configuration](#part-1-email-configuration)
  * [Introduction](#introduction)
    + [Objective](#objective)
    + [Pre-requisites](#pre-requisites)
  * [1. Setup test email account (Gmail example)](#1-setup-test-email-account--gmail-example-)
  * [2. Email Entry Point creation](#2-email-entry-point-creation)
  * [3. Email Queue creation](#3-email-queue-creation)
  * [4. Entry point routing strategy creation](#4-entry-point-routing-strategy-creation)
  * [5. Queue routing strategy creation](#5-queue-routing-strategy-creation)
  * [6. Email Template creation](#6-email-template-creation)
  * [7. Customer sends an Email](#7-customer-sends-an-email)
  * [8. Agent Desktop experience](#8-agent-desktop-experience)
- [Part 2: Chat Configuration](#part-2-chat-configuration)
  * [Section 1 Configuration in WxCC Portal](#section-1-configuration-in-wxcc-portal)
    + [Objective](#objective-1)
    + [Pre-requisites](#pre-requisites-1)
    + [1. Chat Entry Point creation](#1-chat-entry-point-creation)
    + [2. Chat Queue creation](#2-chat-queue-creation)
    + [3. Multimedia Profile creation](#3-multimedia-profile-creation)
    + [4. Assign the team setup to handle chat to the agent](#4-assign-the-team-setup-to-handle-chat-to-the-agent)
  * [Section 2 Chat Template configuration](#section-2-chat-template-configuration)
    + [Objective](#objective-1)
    + [Pre-requisites](#pre-requisites-1)
    + [1. Chat template creation](#1-chat-template-creation)
    + [2. Entry point routing strategy creation](#2-entry-point-routing-strategy-creation)
    + [3. Queue routing strategy creation](#3-queue-routing-strategy-creation)

# Part 1: Email Configuration

## Introduction

<iframe width="560" height="315" src="https://www.youtube.com/embed/FGbDmz3lrhk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Objective

This lab is designed to ensure we onboard Email account configuration in to WxCC. You will be able to initiate an email to the Contact Centre and be able to accept/respond to the email by logging in as an agent.  

We will be configuring Email Account settings, Entry Point, Queue, corresponding Routing strategies, Routing rules and Email Template. This helps us connecting the Email account with our application.  

### Pre-requisites

1. An Email account to be used in WxCC.
2. Portal and Agent Desktop URL.
3. Admin credentials to configure.
4. Agent Credentials to Handle the Email.

## 1. Setup test email account (Gmail example)

Customer/Partner should have an Email account that can be used in WxCC for polling and handling the emails. It can be a Gmail account or Office 365 account.

• If a Gmail account is used, we need to enable POP3/IMAP setting. 
• Login to the Gmail account with the credentials -> Click on settings icon on top right corner -> Select “See all settings”
• Now Click on “Forwarding and POP/IMAP” and enable the “POP Download” and “IMAP access” as in screenshot
• Click on “Google Apps” icon on top right corner -> Select “Account”
• Select “Security” option and turn “ON” the “Less secure app access”
• Use this [link](https://accounts.google.com/b/0/DisplayUnlockCaptcha) to disable captcha for the account and click Continue

## 2. Email Entry Point creation

• Customer admin logins to [WxCC Portal](https://portal.cjp.cisco.com)  with the credentials and accesses the menu ‘Provisioning -> Entry Point/Queues -> Entry Point’.
• Select “New Entry Point” and enter the respective values and click save

## 3. Email Queue creation

• Customer admins access the menu ‘Provisioning -> Entry Point/Queues -> Queue’
• Select “New Queue” and enter the respective values and click save

## 4. Entry point routing strategy creation

• Customer admins access the menu and clicks ‘Routing Strategy’ which cross launches the routing strategy page.
• Select the ‘email entry point’ that you created from the drop down and click on ‘New Strategy’ button 
• Enter the Routing strategy name and proceed to configure the account connection setting by clicking “Add Email Account”
• Configure your support email account and save
• Now click on ‘Add Routing Rule’ and enter your routing rules and save. The content in the subject line helps in subject line-based routing. A combination of ‘And’ and ‘Or’ rules can be applied. However, both ‘And’ and ‘Or’ can’t be added to the same rule.
• Select the queue from the drop-down list for the default routing queue and click save

## 5. Queue routing strategy creation

• Now from the routing strategy page, select the ‘queue’ that you created and click on ‘New Strategy’ button 
• Enter the Queue Name and Select the ‘Routing Type’ from the drop down.
• Enter the 'Time Settings', 'Advanced settings' and 'Email Distribution’ by selecting 'Add Group'.
• Select the Team to which the contact should be delivered and click save group.
• Now click save to complete Queue routing strategy settings. 

## 6. Email Template creation

• Now from the routing strategy page, select the ‘resources’ menu at the top and then choose ‘Predefined Emails’.
• Now click on the ‘New’ button
• Use the insert macro’s option to add the customer name and agent name and their defaults. Also add text as appropriate to the template and save. The template will now be available to all agents to use.

**Note:** A Predefined Email provides agents with an email outline that can be modified or sent directly to customers. There is currently a limit of one Predefined Email per organization. If its status is set to Active, the Predefined Email will automatically appear in all new agent emails. 

## 7. Customer sends an Email

• Customer sends an email to the support email address that was initially configured in the Entry point routing strategy creation.

## 8. Agent Desktop experience

• Once the agent goes Available, the Email will be offered to the agent.
• Click "Accept" to handle the email.
• Click "Reply" or Reply All" to reply to the email and enter the body of the email and hit send button
• Add wrap up and close the task


# Part 2: Chat Configuration


## Section 1 Configuration in WxCC Portal

<iframe width="560" height="315" src="https://www.youtube.com/embed/PsK4DqSgtb8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Objective

This section will guide you through the process of creating Entry Point/Queue/MultimediaProfile entities used in chat configuration on WxCC. 

We will be configuring Entry Point, Queue, Multimedia Profile. 

### Pre-requisites

1. Portal URL.
2. Admin credentials to configure

### 1. Chat Entry Point creation

* Customer admin logs in to [WxCC Management Portal](https://portal.cjp.cisco.com)  with the credentials and accesses the menu 'Provisioning -> Entry Point/Queues -> Entry Point'.
* Select “New Entry Point” and enter the respective values and click save.

### 2. Chat Queue creation

* Customer admins accesses the menu 'Provisioning -> Entry Point/Queues -> Queue'.
* Select “New Queue” and enter the respective values and click save.

### 3. Multimedia Profile creation

* Customer admins accesses the menu 'Provisioning -> Multimedia Profiles -> New Multimedia Profile'.
* Enter the respective values and click save.

### 4. Assign the team setup to handle chat to the agent
* Customer admin accesses the menu ‘Provisioning -> Users'.
* Select 'Users' and edit the agent user to assign the specific team to the user
* Click save.

## Section 2 Chat Template configuration


<iframe width="560" height="315" src="https://www.youtube.com/embed/WGjbBwupBx0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Objective

This section will guide you through the chat template configuration on WxCC.   

### Pre-requisites

1. Control Hub URL and WxCC Portal URL
2. Admin credentials to configure.

### 1. Chat template creation
* Customer admin launches [Webex Control Hub](https://admin.cisco.com)  
* Provide the same email as provided at the time of login to WxCC Portal, when prompted at Control Hub login page.
* From the left hand side menu select "Contact Center" -> select "Features" option from the top right options.
* Select "New" -> "Chat Template" -> "Enter a name for you to identify this template" -> Select the preconfigured entry point -> Click the blue arrow icon on right to go to next page.
* Under "Template Overview" select the requisite options to design customer side chat window preview-> Click the blue arrow icon on right to go to next page.
* On "customer information" page select the requisite options to design the customer side chat window preview -> Click the blue arrow icon on right to go to next page.
* Select the requisite attributes to create the "Off-Hours" customer side chat window preview -> Click the blue arrow icon on right to go to next page.
* Select the requisite attributes to design the Feedback preview, this screen is used to collect feedback from a customer after the chat ends -> Click the blue arrow icon on right to go to next page.
* On "Branding and Identity" page select the requisite attributes to setup customer side chat window preview -> Click the blue arrow icon on right to go to next page.
* On "Status Messages" page configure the status messages to display in the customer chat window for different statuses "Waiting/Chatting/Left the Chat" -> Click the blue arrow icon on right to go to next page.
* Click on Finish to complete the setup.
* Select "Download Embed Code" option to save the Chat_Code_Snippet. This can used to launch the chat from any JS editor like [this](https://www.w3schools.com/tags/tryit.asp?filename=tryhtml_link_image)


### 2. Entry point routing strategy creation

* Go back to WxCC Portal and access and click ‘Routing Strategy’ which cross launches the routing strategy page.
* Select the ‘chat entry point’ that you created from the drop down and click on ‘New Strategy’ button.
* Enter the Routing strategy name.
* Assign the chat queues and save.


### 3. Queue routing strategy creation

* Now from the routing strategy page, select the ‘queue’ that you created and click on ‘New Strategy’ button.
* Enter the Routing strategy name and select the ‘Routing Type’ from the drop down.
* Enter the 'Time Settings', 'Advanced settings' and 'Chat Distribution’ by selecting 'Add Group'.
* Select the Team to which the contact should be delivered and click save group.
* Now click save to complete Queue routing strategy settings. 


Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release on chat section| Naveen Kumar Narasimhan Almeti (naveenkn) | 08 Jan 2021 |
| 2.0 | Formating changes | Mike Turnbow | 08 Jan 2021 |
| 3.0 | Merged Email and Chat parts into same lab | Abhishek Singh (asingh9) | 21 Jan 2021 |
