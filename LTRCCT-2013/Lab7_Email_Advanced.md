---
title: 'Lab 7: Advanced Email Configuration'
---

# Table of Contents
- [Step 1. Email Workflow Overview](#step-1-email-workflow-overview)
- [Step 2. Position In Queue Configuration](#step-2-position-in-queue-configuration)
- [Step 3. Autoreply Configuration](#step-3-autoreply-configuration)
- [Step 4. Enhancing Routing based on a Subject](#step-2-enhancing-routing-based-on-a-subject)
- [Step 5. Integration with Smartsheet using smartsheet APIs](#step-5-integration-with-smartsheet-using-smartsheet-apis)
- [BONUS TASK - Integration with Webex Teams (Alarm notification)](#bonus-task-integration-with-webex-teams-alarm-notification)


# Introduction

### Lab Objective

This lab will give you a detailed understanding of the workflow logic. With that, you will be able to improve the script and do a more advanced configuration. This lab includes multiple script customizations and shows how to create an HTTP Request which is needed for integration with external HTTP services (as an example it uses smartsheet and Webex APIs).


### Pre-requisite

- You have successfully compleated the Lab1 and Lab2 (Email Configuration).

# Lab Section

## Step 1. Email Workflow Overview

Before proceeding with the configuration task, you need to understand the flow logic. Please follow the diagram below and call the proctor if you have any questions.

<img align="middle" src="images/Lab7_workflow.png" width="1000" />
<br/>
<br/>

## Step 2. Position In Queue Configuration
In this task, we will use the predefined node **PIQ and EWT**. This node provides the caller’s current Position in Queue (PIQ) and the Estimated Wait Time (EWT). The flow developer can use these variables with flow logic to determine agent availability in a queue and route elsewhere when needed. The node has three types of output flow branches. These branches get triggered based on return status and values of EWT and PIQ.
  - **Success**: Triggered when both EWT and PIQ APIs succeed and return nonnegative values.
  - **Insufficient Information Flow**: Triggered when the PIQ API returns a valid variable value, and EWT has the value as -1. 
  - **Failure**: This branch is triggered when PIQ API or EWT API fail and/or return invalid values. 

> **Note:** PIQ/EWT node can currently be used only after the Queue Task Node.

- Go to the **Services - My First Service** and open the **Email Inbound Flow**.

- Click on the **EDIT** button in the upper right corner.

- Drug and drop the **PIQ and EWT** node from the Node Palette to the main canvas.

<img align="middle" src="images/Lab7_workflow2.png" width="1000" />
<br/>
<br/>

- Delete the existing **Queue Task** `Queued` link by clicking on it and pressing the delete button. Re-connect the **Queue Task** with the **PIQ and EWT**

<img align="middle" src="images/Lab7_workflow3.png" width="1000" />
<br/>
<br/>  

- You will have to set the Queue ID in the PIQ node. Copy the Queue ID from the **[Management Portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}** -> **_Provisioning_** -> **_Entry Points/Queues_** -> **_Queue_**

<img align="middle" src="images/Lab7_QueueID.png" width="1000" />
<br/>
<br/>

- Go back to Webex Connect and double click on the **PIQ and EWT** node. Set up the following configuration:

| **Setting's Name** | **Value**                       |
| ------------- | ------------------------------------ | 
| METHOD NAME         | Fetch Position in Queue | 
| NODE RUNTIME AUTHORIZATION    | WxCC Authorization | 
| QUEUE ID    | \<Queue ID from Managment Portal\> | 
| TASK ID    | $(n1850.Task ID) | 
| LOOKBACK MINUTES    | 5 | 
  
<img align="middle" src="images/Lab7_workflow4.png" width="1000" />
<br/>
<br/>

- Click **SAVE** and link all exit states of **PIQ and EWT** with **Update Conversation**.
  
<img align="middle" src="images/Lab7_workflow5.png" width="1000" />
<br/>
<br/>

## Step 3. Autoreply Configuration
  
In the default script, the autoreply is already preconfigured for all new tasks. In this step, we will enhance the answer by adding changing the message and adding the PIQ variable.
  
- Double click on the **Email** node and in the **MESSAGE**. 

<img align="middle" src="images/Lab7_autoanswer1.png" width="1000" />  
<br/>
<br/>

- Set the customized message. Exampel: __Dear $(n2.email.senderName). We have successfully received your request. You have $(n1894.positionInQueue) Position In Queue.__ and click on **SAVE**.
  
> **Note:** Your PIQ node ID can be different from the example above.
  
<img align="middle" src="images/Lab7_autoanswer2.png" width="1000" />  
<br/>
<br/>

- Publish your workflow by clicking on **SAVE** and **MAKE LIVE**.
  
- Make sure that the agent is in **IDLE** state in the Agent Desktop.
 
- Go to your personal email account or ask the proktor to send 2 emails with different subject to the configured email address.

- Wait for 1 minute and check the auto response, you should see your PIQ.
  
  
## Step 4. Enhancing Routing based on a Subject
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

- Click on **EDIT** button in the upper right corner.
 
- Drug and drop the **Branch** node from the Node Palette to the main canvas.

<img align="middle" src="images/Lab7_subject1.png" width="1000" />  
<br/>
<br/>

- Delete the existin **Create Task** **Created** link by clickin on it and pressing delete button. Re-connect **Create Task** with **Branch**
  
<img align="middle" src="images/Lab7_subject2.png" width="1000" />  
<br/>
<br/>

- Double click on the **Branch** node and set the following conditions for Branch1: 
  
| **Setting's Name** | **Value**                       |
| ------------- | ------------------------------------ | 
| Variable    | $(n2.email.subject) | 
| CONDITION   | Regular expression (RegEx) | 
| VALUE    | [cC][iI][sS][cC][oO]\s[lL][iI][vV][eE] | 

 
<img align="middle" src="images/Lab7_subject3.png" width="1000" />  
<br/>
<br/>

- Drug and drop the **Email** node from the Node Palette to the main canvas. Connect exit **Branch1** with **Queue Task** and **None of the above** exit with the **Email**

<img align="middle" src="images/Lab7_subject4.png" width="1000" />  
<br/>
<br/>

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
<br/>
<br/>

- Click on **SAVE** and link all exit events for the **Email** with the **Close Task**

<img align="middle" src="images/Lab7_subject6.png" width="1000" />  
<br/>
<br/>

- Publish your workflow by clicking on **SAVE** and **MAKE LIVE**.
  
- Go to your personal email account or ask the proctor to send 2 emails (with and without the "Cisco Live" subject).

- As a result, only 1 email should come into the Email queue. Wait for 1 minute and check the auto replies, 1 email should come with PIQ autoreply, another one with the "no Cisco Live in subject" message.

  
## Step 6. Integration with Smartsheet using smartsheet APIs
In this task, you will learn how to work with HTTP Request node. As the example we are going to use a smartsheet API. Smartsheet APIs allow you to programmatically access and manage Smartsheet data especially read and update sheets.

In our case, if the subject does not contain "Cisco Live" we will be adding a new row with the details in this smartsheet table: https://app.smartsheet.com/sheets/mGxggWGV8qcxmxvgcvRmfjxqfhcCFwGg4RHmQP71?view=grid

### 1. Preconfigured settings
The 3 steps below were **preconfigured** for you. They has to be done only once.
>1) The smartsheet API key has been generated according to the guide https://smartsheet.redoc.ly/#section/API-Basics/Raw-Token-Requests

<img align="middle" src="images/Lab7_smartsheet1.png" width="1000" />  
<br/>
<br/>

> 2) The smartsheet grid was created. And Columns’ ID were collected through API (we will need it for the API request when we will be adding a new row).

<img align="middle" src="images/Lab7_smartsheet2.png" width="1000" />  
<br/>
<br/>

> 3) We checked that we are able to add a row through the postman acording to the documentation: https://smartsheet.redoc.ly/#operation/rows-addToSheet
It needs just for the verification, exactly the same we will be doing in the Email Workflow with HTTP Request node.
  
<img align="middle" src="images/Lab7_smartsheet3.png" width="1000" />  
<br/>
<br/>

### 2. HTTP Request configuration  

- First Click on **EDIT** button in the upper right corner.
  
- Drug and drop the **HTTP Request** node from the Node Palette to the main canvas. Connect exit **Email** with **On Success** with the **HTTP Request**

<img align="middle" src="images/Lab7_smartsheet4.png" width="1000" />  
<br/>
<br/>

- Double click on the **HTTP Request** node, set the following settings and click **SAVE**.
  
| **Setting's Name** | **Value**                       |
| ------------- | ------------------------------------ | 
| METHOD    | POST | 
| ENDPOINT URL   | https://api.smartsheet.com/2.0/sheets/6430831221729156/rows | 
| Authorization    | Bearer XXXXXXXXXXXXXXXXXX |   
| Content-Type    | application/json |   
| TIMEOUT    | 3000 |   

**BODY:**
```
{
    "cells": [
      {
        "columnId": 8617723039115140,
        "value": "$(n2.email.senderName)",
        "strict": false
      },
      {
        "columnId": 4114123411744644,
        "value": "$(n2.email.emailId)",
        "strict": false
      },
      {
        "columnId": 4958548341876612,
        "value": "$(n2.email.subject)",
        "strict": false
      }
    ]
  }
```

  
<img align="middle" src="images/Lab7_smartsheet5.png" width="1000" /> 
<br/>
<br/>

- Connect all exits with **Close Task** node.

<img align="middle" src="images/Lab7_smartsheet6.png" width="1000" /> 
<br/>
<br/>

- Publish your workflow by clicking on **SAVE** and **MAKE LIVE**.
  
- Go to your personal email account or ask the proctor to send 1 email without the "Cisco Live" subject.

- After 1 minute check the smartsheet table. The row with the email details has to appear: https://app.smartsheet.com/sheets/mGxggWGV8qcxmxvgcvRmfjxqfhcCFwGg4RHmQP71?view=grid
  
 
## BONUS TASK - Integration with Webex Teams (Alarm notification)
The idea is to show that you can integrate the Flow with Webex Teams and this can be used as the notifications for supervisors based on the specific criteria.
This section has the bonus category where we can check how you understand this topic. Here we give you the task without a step-by-step explanation the result will be the message from the Webex bot in our Cisco Live space. 

**Use case:** As a supervisor, I want to get the notifications in the Webex Teams if there are more then 3 email in queue (PIQ).

1) The Webex API token is generated for you
  
<img align="middle" src="images/Lab7_webex1.png" width="1000" />   
<br/>
<br/>

2) Here is the example of the Postman request

<img align="middle" src="images/Lab7_webex2.png" width="1000" /> 
<br/>
<br/>

3) **HTTP Request** node settings: 
  
| **Setting's Name** | **Value**                       |
| ------------- | ------------------------------------ | 
| METHOD    | POST | 
| ENDPOINT URL   | https://webexapis.com/v1/messages | 
| Authorization    | Bearer XXXXXXXXXXXXXXXXXX |   
| Content-Type    | application/json |   
| TIMEOUT    | 3000 |   

**BODY:**
```
{
    "roomId":"Y2lzY29zcGFyazovL3VzL1JPT00vYzI5ODg1ZDAtZDg3ZC0xMWVjLTk2ZjQtZmQzNzA1YTFjMGJi",
    "text":"There are more than $(nX.positionInQueue) tasks in queue!"
}
```

<img align="middle" src="images/Lab7_webex3.png" width="1000" /> 
<br/>
<br/>
 

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
