---
title: 'Lab 7: Advanced Email Configuration'
---

# Table of Contents
- [Step 1. Email Workflow Overview](#step-1-gmail-account-configuration)
- [Step 2. Position In Queue Configuration](#step-1-gmail-account-configuration)
- [Step 3. Autoreply Configuration](#step-1-gmail-account-configuration)
- [Step 4. Enhancing Routing based on the Subject](#step-2-create-email-asset-and-register-to-webexcc)
- [Step 5. Integration with Smartsheet using smartsheet APIs](#step-4-createupload-email-flow)


# Introduction

### Lab Objective

This lab will give you a detailed understanding of the predefined workflow logic. With that, you will be able to improve the script and do a more advanced configuration.
This lab includes multiple script customizations and shows how to create an HTTP Request which is needed for integration with external HTTP services (as an example it uses smartsheet API).


### Pre-requisite

- You have successfully compleated the Lab1 and Lab2 (Email Configuration).

# Lab Section

## Step 1. Email Workflow Overview

Before proceeding with the configuration task, you need to understand the flow logic. Please follow the diagram below and call the proctor if you have any questions.

<img align="middle" src="images/Lab7_workflow.png" width="1000" />



## Step 2. Position In Queue Configuration
In this task we will use the predefined node **PIQ and EWT**. This node provides the caller's current Position in Queue (PIQ) and the Estimated Wait Time (EWT). The flow developer can use these variables with flow logic to determine agent availability in a queue and route elsewhere when needed.
The node has three types of output flow branches. These branches get triggered based on return status and values of EWT and PIQ.
  - Success: Triggered when both EWT and PIQ APIs succeed and return nonnegative values.
  - Insufficient Information Flow: Triggered when the PIQ API returns a valid variable value, and EWT has the value as -1. 
  - Failure: This branch is triggered when PIQ API or EWT API fail and/or return invalid values. 

> **Note:** PIQ/EWT node can currently be used only after the Queue Task Node.

- Go to the **Services - My First Service** and open the **Email Inbound Flow**.

- Click on **EDIT** button in the upper right corner.

- Drug and drop the **PIQ and EWT** node from the Node Palette to the main canvas.

<img align="middle" src="images/Lab7_workflow2.png" width="1000" />

- Delete the existin **Queue Task** **Queued link** by clickin on it and pressing delete button. Re-connect **Queue Task** with **PIQ and EWT**

<img align="middle" src="images/Lab7_workflow3.png" width="1000" />

- You will have to set the Queue ID in the PIQ node. Copy the Queue ID from the **[Management Portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}** -> **_Provisioning_** -> **_Entry Points/Queues_** -> **_Queue_**

<img align="middle" src="images/Lab7_QueueID.png" width="1000" />

- Go back to Webex Connect and double click on the **PIQ and EWT** node. Set up the following configuration:

| **Setting's Name** | **Value**                       |
| ------------- | ------------------------------------ | 
| METHOD NAME         | Fetch Position in Queue | 
| NODE RUNTIME AUTHORIZATION    | WxCC Authorization | 
| QUEUE ID    | <Queue ID from Managment Portal> | 
| TASK ID    | $(n1850.Task ID) | 
| LOOKBACK MINUTES    | 5 | 
  
<img align="middle" src="images/Lab7_workflow4.png" width="1000" />

- Click **SAVE** and link all exit states of **PIQ and EWT** with **Update Conversation**.
  
<img align="middle" src="images/Lab7_workflow5.png" width="1000" />


Step 3. Autoreply Configuration
  
In the default script, the autoreply is already preconfigured for all new tasks. In this step, we will enhance the answer by adding changing the message and adding the PIQ variable.
  
- Double click on the **Email** node and in the **MESSAGE**. 

<img align="middle" src="images/Lab7_autoanswer1.png" width="1000" />  

- Set the customized message. Exampel: __Dear $(n2.email.senderName). We have successfully received your request. You have $(n1894.positionInQueue) Position In Queue.__ and click on **SAVE**.
  
> **Note:** Your PIQ node ID can be different from the example above.
  
<img align="middle" src="images/Lab7_autoanswer2.png" width="1000" />  

- Publish your workflow by clicking on **SAVE** and **MAKE LIVE**.
  
- Make sure that the agent is in **IDLE** state in the Agent Desktop.
 
- Go to your personal email account or ask the proktor to send 2 emails with different subject to the configured email address.

- Wait for 1 minute and check the auto response, you should see your PIQ.
  
  
## Step 4. Enhancing Routing based on the Subject
In this task, you will be checking the **Subject** for **Cisco Live** text. If it is not there, the task will be closed with the auto-reply message "There is no Cisco Live text in your subject".
The branch node allows you to split your flow based on conditional statements without the need to write any custom code. You can configure multiple branches within a single node. The node uses a top-down sequential approach to evaluate the conditions. The supported conditions are:
    - Equals
    - Not equals
    - Less than
    - Greater than
    - Less than or equals
    - Greater than or equals
    - Regular expression (RegEx)
    - Equals ignore case
    - Contains
    - Contains ignore case
    - In
    - Not in
    - Starts with
    - Ends with
    - Between

 
- Drug and drop the **Branch** node from the Node Palette to the main canvas.

<img align="middle" src="images/Lab7_subject1.png" width="1000" />  

- Delete the existin **Create Task** **Created** link by clickin on it and pressing delete button. Re-connect **Create Task** with **Branch**
  
<img align="middle" src="images/Lab7_subject2.png" width="1000" />  
  
- Double click on the **Branch** node and set the following conditions for Branch1: 
  
  | **Setting's Name** | **Value**                       |
| ------------- | ------------------------------------ | 
| Variable    | $(n2.email.subject) | 
| CONDITION   | Regular expression (RegEx) | 
| VALUE    | [cC][iI][sS][cC][oO]\s[lL][iI][vV][eE] | 

 
<img align="middle" src="images/Lab7_subject3.png" width="1000" />  
  
- Drug and drop the **Email** node from the Node Palette to the main canvas. And connect exit **Branch1** with **Queue Task** and **None of the above** exit with the **Email**

<img align="middle" src="images/Lab7_subject4.png" width="1000" />  
  
- Double click on the **Email** node and set the following settings: 
  
| **Setting's Name** | **Value**                       |
| ------------- | ------------------------------------ | 
| DESTINATION ID    | $(n2.email.subject) | 
| FROM NAME   | $(n2.email.senderName) | 
| SUBJECT    | $(n2.email.subject) |   
| MESSAGE    | There is no "Cisco Live" text in your subject |   
| HEADER PARAMETER    | In-Reply-To |   
| VALUE    | $(n2.email.messageId) |   
  
<img align="middle" src="images/Lab7_subject5.png" width="1000" />  
  
- Click on **SAVE** and link all exit events for the **Email** with the **Close Task**

<img align="middle" src="images/Lab7_subject6.png" width="1000" />  
  
- Publish your workflow by clicking on **SAVE** and **MAKE LIVE**.
  
- Go to your personal email account or ask the proctor to send 2 emails (with and without the "Cisco Live" subject.

- As a result, only 1 email should come into the Email queue. Wait for 1 minute and check the auto replies, 1 email should come with PIQ autoreply, another one with the "no Cisco Live in subject" message.

  
## Step 6. Integration with Smartsheet using smartsheet APIs
  
  
  
  
### 1. Google Account Setting – Enable POP3/IMAP setting


| **User email**                       |
| ------------------------------------ | 
| cl1webex**\<ID\>**@gmail.com   | 

> **Note:** Your \<ID\> was provided to you personally.  \<ID\> is the unique number equal to your POD.


- Login to the Gmail account with the credentials above[https://mail.google.com](https://mail.google.com){:target="_blank"}. The password is the same as for Webex admin account.

- Enable POP3/IMAP setting by clicking on settings icon on top right corner and selecting **See all settings**.

<img align="middle" src="images/Lab2_Gmail1.png" width="1000" />

- Now Click on **Forwarding and POP/IMAP**, enable the `POP Download` and `IMAP access` then click **Save Changes**.

<img align="middle" src="images/Lab2_Gmail2.png" width="1000" />




[Back to top](#table-of-contents)
---

### Congratulations, you have completed this section! 

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2013/Home.html";}
function nextLab() 
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2013/Lab8_AgentProductivity.html";
 }
</script>

<div id="button-row">
<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Main Page</button>

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Next Lab</button>

</div>
