---
title: "Lab 8: Webex Experience Management"
---

## Overview of the lab:
In this Lab, we will go through the tasks that are required to build a Webex Experience Management connecter and use that to send a survey to customers so that they can provide feedback on their interaction with the contact center. Also, we will look at how the agent can get this feedback on their agent desktop to provide appropriate level of service to end customers. This will enhance their customer satisfaction level which will positively impact their business.


# Table of Contents

- [Part 1: WxM Connector setup](#part-1-wxm-connector-setup)
  * [a) Identify the API key from WxM](#a-identify-the-api-key-from-wxm)
  * [b) Configure WxM connector in Control hub](#b-configure-wxm-connector-in-control-hub)
- [Part 2: Onboarding CH Agent as WxM User](#part-2-onboarding-ch-agent-as-wxm-user)
  * [**IMPORTANT : Before You Begin**](#important--before-you-begin)
  * [a) Create WxM User and Generate API key](#a-create-wxm-user-and-generate-api-key)
  * [b) Identify Org ID, CH User ID and email of Agent](#b-identify-org-id-ch-user-id-and-email-of-agent)
  * [c) Run WxM OnBoard API](#c-run-wxm-onboard-api)
- [Part 3: Enable WxM widgets in Desktop Layout](#part-3-enable-wxm-widgets-in-desktop-layout)
  * [Pre-requisites](#pre-requisites)
  * [a) Enable wxmConfigured flag](#a-enable-wxmconfigured-flag)
  * [b) Enable Customer Experience Journey Widget](#b-enable-customer-experience-journey-widget)
  * [c) Enable Customer Experience Analytics Widget](#c-enable-customer-experience-analytics-widget)
  * [d) Test Voice, Email and Chat Interaction](#d-test-voice--email-and-chat-interaction)
- [Part 4: Configure Feedback node in Flow](#part-4-configure-feedback-node-in-flow)
  * [Pre-requisites](#pre-requisites-1)
  * [a) Configure Feedback Node](#a-configure-feedback-node)
  * [b) Test Voice interaction and confirm that the survey is received by the caller's email](#b-test-voice-interaction-and-confirm-that-the-survey-is-received-by-the-callers-email)
  * [c) Validate that the survey filled by the caller is recorded properly in WxM](#c-validate-that-the-survey-filled-by-the-caller-is-recorded-properly-in-wxm)

# Introduction

## Lab Objective
- **Explore the WxM console** and its features

- Edit the **Desktop Layout for configuring the WxM widget**

- Learn how to configure a **flow for geting feedback**
 

## Pre-requisites

1. You have **completed Lab 1 - Control Hub & Admin Portal:**
 - You are familiar with how to create a new user in Control Hub


2. You have **completed Lab 2 - IVR Contact Routing:**
 - You are familiar with creating and modifying flows


3. You have **completed Lab 3 - Agent and Supervisor Desktops:**
 - You are familiar with editing and updating desktop layout JSON


4. You have **Webex Calling installed** in your mobile phone and supervisor created in Lab 1 from which you can make calls to the contact center



## Quick Links
> Control Hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="_blank"}**\
> WxM Console **[https://cx.cloudcherry.com](https://cx.cloudcherry.com){:target="_blank"}**


# Lab Section

> Due to limitation with the number of WxM tenants, all the participants will use the same tenant (**Pod29**) for this lab.

| **Account** | **Username**      | **Password**                   |
| ----------- | ----------------- | -------------------------------- |
| WxM admin       | wxmdemoadmin   | Login@123 |
| Pod29 admin         | admin1pod29@email.carehybrid.com  | ReadyNext2021! |


## Part 1: WxM Connector setup -- Not need to complete it, already configured

* **We have configured the WxM Connector for you**. 
* You just need to login in Control Hub with Pod29 credentials, navigate to _Services -> Contact Center -> Connectors_ and **check that the WxM Connector is already created**.
* However, we recommend you to **have a look to the video and configuration steps below**, to get an idea of how WxM Connector is configured



>The following video outlines the steps required to create the WxM connector. WxCC uses this connector to read the dispatches that are configured in WxM. This connector is also used to load the widgets into the agent desktop and FeedBack is triggered via the same.

<iframe width="1024" height="576" src="https://youtube.com/embed/GI4nzVLLFCk?rel=0" title="WxM Lab" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 1. Identify the API key from WxM

* Login to the [WxM console](https://cx.cloudcherry.com)
* Enter the admin credentials.
* Dismiss informative alerts if any.
* Click on the User Profile (Top) icon and then Edit Profile
* Copy the API Key from the API Key section.
* If the API key is not present, click on Create and then copy the key.

### 2. Configure WxM connector in Control hub

* Login to [Control Hub](https://admin.webex.com)
* Enter the Customer admin email id and the password.
* Navigate to **_Contact Center_** Card
* Click on **_Connectors_**
* Click on Set Up on Webex Experience Management card.
* Provide a unique identifier in the Name text area
* Provide the WxM admin Username
* Paste the API Key (copied above)
* Click on Save and then Close.


## NOT NEEDED

## Part 2: Onboarding CH Agent as WxM User

The following video demos how a Control Hub user is onboarded to WxM. We have to ensure that each of the agents in Control Hub is linked to one of the valid users in WxM. Based on the access of the WxM user, appropriate widgets will be loaded into Agent Desktop. Since the access control is based on the WxM user, this step is very critical.

<iframe width="1024" height="576" src="https://youtube.com/embed/SmRBu4QFCos?rel=0" title="Onboarding WxM Lab" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### **IMPORTANT : Before You Begin**

* Please create a new agent in Control Hub with an email inbox to which you have access.
* The below steps will need you to activate a user and hence the request for an inbox to which you have access to click the user activation link.
* We will use this agent to login to Agent Desktop and handle voice calls, Email interaction, and Chat interaction.
* Hence ensure that the configured agent profile has required channels and is part of the voice, email & chat queue, and the respective Team


* Input the UserID, OrgID, and EmailID values which you have noted down from the above steps.
* Ensure that the API request Accept and Content-Type Headers are set to "application/JSON"
* Click the button to trigger the API request.

## Part 2: Create new agent in CH
* Login in the **[Control Hub](https://admin.webex.com)** with credentials of **Pod29**
* Create and activate a new agent with the following naming convention: **`WxM_Agent_<ID>_TS`**
* Make sure you **activate Webex Calling and give an extension number**, like you did in Lab 1 - Control Hub & Admin Portal 
* Navigate to the **[Tenant Portal](https://portal.wxcc-us1.cisco.com/portal)** and create **``Team1_<ID>_TS``** for your Agent
* Add your team to the Queue Distribution Group
 
## Part 3: Enable WxM widgets in Desktop Layout

>The following video demos how the Agent Desktop Layout JSON has to modify with the appropriate values of the WxM dashboard so that they are loaded into the widgets. The Space ID and the Metrics ID extracted from WxM decide which widget will be loaded for the agent. This lab section assumes that you are familiar with how the agent desktop layout can be modified and applied to a team.

<iframe width="1024" height="576" src="https://youtube.com/embed/Njie8PrB6Kk?rel=0" title="Enabling WxM Widgets" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 1. Enable wxmConfigured flag

* **Download the current desktop default layout** of the team used by the newly created Agent.
* Edit the JSON file in an editor and search for the key **_wxmConfigured_**.
* If not changed already, change the value to **True**

### 2. Enable Customer Experience Journey Widget

* Login to the **[WxM console](https://cx.cloudcherry.com)** with the WxM admin credentials
* Enter the **WxM admin credentials**.
* Dismiss informative alerts if any.
* Navigate to the **Overall Experience** response page.
* Click the Vertical Ellipsis on the right side of the screen and **Export To Cisco Contact Center**
* From the information pane, **copy the Space Id** and update this in the **Customer Experience Journey section** of the layout JSON.
* Since Customer Experience Journey, does not have metricsId **you can use the space Id copied here as the metrics Id**. Else you can the metrics Id of Customer Experience Analytics and paste it here (which you will get in the below steps)

### 3. Enable Customer Experience Analytics Widget

* Navigate to the **Agent Dashboard** page.
* Make sure you have **Customer Experience Analytics** selected in the top-left corner
* Click the Vertical Ellipsis on the right side of the screen and **Export To Cisco Contact Center**
* From the information pane, copy the **Space Id** and update this in the **Customer Experience Analytics section** of the layout JSON.
* From the information pane, copy the **Metrics Id** and update this in the **Customer Experience Analytics section** of the layout JSON.
* Save this JSON file and **upload** it in the appropriate layout used by the Test Agents Team.
* Now if you login as an agent and test Voice interactions, you will be able to access both the Customer Experience Analytics widget and Customer Experience Journey widget.

### 4. Check Widgets in Agent Desktop

* Login in the **[Agent Desktop](https://desktop.wxcc-us1.cisco.com){:target="_blank"}**\ with the recently created agent credentials
* Confirm that the WxM widgets are loaded on Agent Desktop and are visible.


## Part 4: Configure Feedback node in Flow

* We have created the Flow and configured the Feedback node for you.
* Login in the Tenant Portal, navigate to Routing Strategies and open the Flow to see how the Flow Diagram is buit.
* You can also see the video and the **Configure Feedback Node** section to see the configuration steps needed.



>The following video does a quick demo on how the FeedBack node should be implemented such that the caller receives an email with the survey link after completion of the call. The same steps can be followed to trigger an SMS with the survey link to the call ANI. Since Email and Chat are not integrated with Flow, Feedback cannot be used for those interactions. 

<iframe width="1024" height="576" src="https://youtube.com/embed/qGW6lRI7AA0?rel=0" title="Configure Feedback Node" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 1. Configure Feedback Node

* Login to portal with admin credential and navigate to `Routing Strategy`
* Click on `Flows` and edit the flow used in the call flow.
* Create 2 custom variables and hardcode values that will be used as `Customer ID` and `Email`.
* Navigate to `Event Flows` and insert `Feedback` node after `ContactEnded` event.
* Input `Activity Label` of your choice and select `Demo Email` from the `Dispatch` dropdown.
* Select `Set Language` to `English (US)` and select appropriate values for `Customer ID` and `Email`.
* For `Phone Number`, select the built-in flow variable `NewPhoneContact.ANI`
* Ensure that the `Feedback` nodes are connected properly with end nodes and `Validation` passes. Publish the change by clicking the `Publish Flow` button.

### 2. Test Voice interaction and confirm that the survey is received by the caller's email

* Login to the recently created agent who has been OnBoarded in WXM.
* Trigger a voice call and ensure that the call connects to the agent
* End the call from the Agent
* They should call you for getting voice survey

### 3. Validate that the survey filled by the caller is recorded properly in WxM

* Login to the **[WxM console](https://cx.cloudcherry.com)**
* Enter the **WxM admin credentials.**
* Navigate to the **`Overall Experience`** dashboard and ensure that the feedback you provided is recorded


