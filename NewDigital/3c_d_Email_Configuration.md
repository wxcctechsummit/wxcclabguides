---
title: 'Lab 3(c,d): Email Configuration'
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/ESaqR2Mwnww" title="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents
- [Lab 3c - Asset creation end to end (Mail)](#Lab-3c---Asset-creation-end-to-end-(Mail))
    * Email account settings
    * Create Email Asset and Register to WebeXCC
    * Add forwarding Address 
    * Create EP/Q

- [Lab 3d - Workflow association(Mail)](#Lab-3d---Workflow-association(Mail))
    * Create/Upload Email flow
    * Add Authorizations for each of the Engage and WxCC nodes
    * Demo 

# Introduction

## Lab Objective

This lab is designed to ensure we onboard Email account configuration into WxCC using IMI. You will be able to initiate an email to the Contact Center and be able to accept/respond to the email by logging in as an agent.  

We will be configuring Email Account settings, Email Assets, Entry Point, Queue and corresponding workflows. This helps us connecting the Email account with our application.  

## Pre-requisite

1. An Email account to be used in WxCC.
2. Portal, Agent Desktop and IMI connect URL.
3. Admin credentials to configure in portal and IMI connect.
4. Agent Credentials to Handle the Email.

# Lab 3c - Asset creation end to end (Mail)

## 1. Organization admin – sets up support email account

• Customer/Partner should have an Email account that can be used in WxCC for polling and handling the emails. It can be a Gmail account or Office 365 account or any account which has email forwarding.


## 2. Gmail account – Enable POP3/IMAP setting

- If a Gmail account is used, we need to enable POP3/IMAP setting. 

- Login to the Gmail account with the credentials -> Click on settings icon on top right corner -> Select “See all settings”.

- Now Click on “Forwarding and POP/IMAP” and enable the “POP Download” and “IMAP access” and click save.


## 3. Google Account Setting – Security setting (allow less secure app access)

- Click on “Google Apps” icon on top right corner -> Select “Account”

- Select “Security” option and turn “ON” the “Less secure app access”

## 4. Disable captcha for the account

- Use the following link to disable captcha for the account https://accounts.google.com/b/0/DisplayUnlockCaptcha and click Continue.

## 5. Create Email Asset and Register to WebeXCC

- Customer admin logs in to IMI connect UI using the URL provided by the IMI team with the credentials. Here for the demo tenant the URL is "https://solutionassuranceesrgt-sa.imiconnect.io/login". 

- Select Assets -> Apps -> Configure New App -> Email and enter the respective values and click test connection.

- Once test is successfully completed, click on save.

- Click on Register to WebeXCC -> Select the appropriate service and click register.

## 6. Add forwarding Address

- Copy the forwarding address from the created asset in previous step and in Gmail account, click on settings icon on top right corner -> Select “See all settings” -> Click on “Forwarding and POP/IMAP” -> click on add a forwarding address -> Paste the copied forwarding address from the created asset and click Next.

- A new pop up tab opens and click proceed and then click OK when it prompts.

- Now in IMI connect, click on Tools -> Export Logs. Under Inbound logs, Select the App that we created -> Select Channel Event as Incoming Email -> Select the period as today and click Download. A log file gets downloaded.

- Open the log file, under the subject column, copy the confirmation code and paste it in the email account for verification and click verify.

- Select Forward a copy of incoming mail to the verified address and click save.


## 7. Email Entry Point creation

- Customer admin logs into “CJP Management Portal” URL with the credentials and accesses the menu ‘Provisioning -> Entry Point/Queues -> Entry Point’.

- Select “New Entry Point” and enter the respective values and click save

## 8. Email Queue creation

- Customer admin accesses the menu ‘Provisioning -> Entry Point/Queues -> Queue’

- Select “New Queue” and enter the respective values and click save

# Lab 3d - Workflow association(Mail)

## 9. Create/Upload Email flow

- Download the template flows from "https://github.com/CiscoDevNet/webexcc-digital-channels" link.

- Select the appropriate data center flows and select the zip file and click download.

- Unzip the downloaded file.

- In IMI connect click on Services and select the service in which the Asset is created in step 5.

- Navigate to Flows -> Create Flow -> Enter the flow name, select the type as work flow and under method select "upload a flow".

- Drag and drop the "Email_Inbound_US.workflow" flow that is downloaded in zip file and click create and then click save.

## 10. Add Authorizations for each of the Engage and WxCC nodes

- Double click on Engage or WxCC node and select the authorization if we already have one, else create a new one under Node Runtime Authorization.

- For Engage node authorization, provide the Authorization Name and client details that was shared by IMI Team upon tenant provisioning and click authorize.

- For WxCC node authorization, provide the Authorization Name and click authorize. This routes to the WxCC login page. Provide the Admin user email address and click sign in.

NOTE: Repeat the step 10 for all Engage and WxCC nodes.

- After adding authorization details, click on save on top right corner.

- Click on settings on top right corner and click Custom variables. Here in bizemailid row, update the email address of the account that is added and click save.

- Finally click on Make Live on top right corner -> Select the Application/Asset that we have created and click Make Live.


## 11. Customer sends an Email

- Customer sends an email to the support email address that was initially configured in the Email Asset creation.

## 12. Agent Desktop – Email offering to an Agent, Acceptance, and closure

- Once the agent goes Available, the Email will be offered to the agent.

- Click "Accept" to handle the email.

- Click "Reply" or Reply All" to reply to the email and enter the body of the email and hit send button

- Add wrap up and close the task.




Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Naveen Kumar Narasimhan Almeti (naveenkn@cisco.com) | 21 Oct 2021 |
| 2.0 | Format Changes | Gagarin JS (gasathiy@cisco.com) | 04 Nov 2021 |


