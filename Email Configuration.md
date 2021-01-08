# Email Configuration

Video example

<iframe width="560" height="315" src="https://www.youtube.com/embed/FGbDmz3lrhk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents

1. Email account settings
2. Create EP/Q
3. Create EP/Q Routing Strategies, Routing Rules
4. Associate Teams to respective Q
5. Create Email template
6. Demo 

# Introduction

## Lab Objective

This lab is designed to ensure we onboard Email account configuration in to WxCC. You will be able to initiate an email to the Contact Centre and be able to accept/respond to the email by logging in as an agent.  

We will be configuring Email Account settings, Entry Point, Queue, corresponding Routing strategies, Routing rules and Email Template. This helps us connecting the Email account with our application.  

## Pre-requisite

1. An Email account to be used in WxCC.
2. Portal and Agent Desktop URL.
3. Admin credentials to configure.
4. Agent Credentials to Handle the Email.


### 1. Organization admin – sets up support email account

Customer/Partner should have an Email account that can be used in WxCC for polling and handling the emails. It can be a Gmail account or Office 365 account.



### 2. Gmail account – Enable POP3/IMAP setting

• If a Gmail account is used, we need to enable POP3/IMAP setting. 
• Login to the Gmail account with the credentials -> Click on settings icon on top right corner -> Select “See all settings”
• Now Click on “Forwarding and POP/IMAP” and enable the “POP Download” and “IMAP access” as in screenshot


### 3. Google Account Setting – Security setting (allow less secure app access)

• Click on “Google Apps” icon on top right corner -> Select “Account”
• Select “Security” option and turn “ON” the “Less secure app access”


### 4. Disable captcha for the account

• Use the following link to disable captcha for the account https://accounts.google.com/b/0/DisplayUnlockCaptcha and click Continue

### 5. Email Entry Point creation

• Customer admin logins to “CJP Management Portal” URL https://portal.cjp.cisco.com  with the credentials and accesses the menu ‘Provisioning -> Entry Point/Queues -> Entry Point’.
• Select “New Entry Point” and enter the respective values and click save

### 6. Email Queue creation

• Customer admins access the menu ‘Provisioning -> Entry Point/Queues -> Queue’
• Select “New Queue” and enter the respective values and click save

### 7. Entry point routing strategy creation

• Customer admins access the menu and clicks ‘Routing Strategy’ which cross launches the routing strategy page.
• Select the ‘email entry point’ that you created from the drop down and click on ‘New Strategy’ button 
• Enter the Routing strategy name and proceed to configure the account connection setting by clicking “Add Email Account”
• Configure your support email account and save
• Now click on ‘Add Routing Rule’ and enter your routing rules and save. The content in the subject line helps in subject line-based routing. A combination of ‘And’ and ‘Or’ rules can be applied. However, both ‘And’ and ‘Or’ can’t be added to the same rule.
• Select the queue from the drop-down list for the default routing queue and click save

### 8. Queue routing strategy creation

• Now from the routing strategy page, select the ‘queue’ that you created and click on ‘New Strategy’ button 
• Enter the Queue Name and Select the ‘Routing Type’ from the drop down.
• Enter the 'Time Settings', 'Advanced settings' and 'Email Distribution’ by selecting 'Add Group'.
• Select the Team to which the contact should be delivered and click save group.
• Now click save to complete Queue routing strategy settings. 

### 9. Email Template creation

• Now from the routing strategy page, select the ‘resources’ menu at the top and then choose ‘Predefined Emails’.
• Now click on the ‘New’ button
• Use the insert macro’s option to add the customer name and agent name and their defaults. Also add text as appropriate to the template and save. The template will now be available to all agents to use.

**Note:** A Predefined Email provides agents with an email outline that can be modified or sent directly to customers. There is currently a limit of one Predefined Email per organization. If its status is set to Active, the Predefined Email will automatically appear in all new agent emails. 


### 10. Customer sends an Email

• Customer sends an email to the support email address that was initially configured in the Entry point routing strategy creation.

### 11. Agent Desktop – Email offering to an Agent, Acceptance, and closure

• Once the agent goes Available, the Email will be offered to the agent.
• Click "Accept" to handle the email.
• Click "Reply" or Reply All" to reply to the email and enter the body of the email and hit send button
• Add wrap up and close the task




Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Naveen Kumar Narasimhan Almeti (naveenkn) | 08 Jan 2021 |
| 1.1 | Formating changes | Mike Turnbow | 08 Jan 2021 |

