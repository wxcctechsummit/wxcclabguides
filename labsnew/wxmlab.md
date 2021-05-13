---
title: "Lab 9: Webex Experience Management"
---

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

In this Lab, we will go through the tasks that are required to build a Webex Experience Management connecter and use that to send a survey to customers so that they can provide feedback on their interaction with the contact center. Also, we will look at how the agent can get this feedback on their agent desktop to provide appropriate level of service to end customers. This will enhance their customer satisfaction level which will positively impact their business.

## Pre-requisites

* You have an assigned POD
* You have the customer admin login credentials.
* You are familiar with how to create a new user in Control Hub
* You have finished earlier labs and are familiar with the application
* Your pod has the required configuration for a chat to route to an agent
* Your pod has the required configuration for an email to route to an agent
* You have configured all the requisites for the agent to log in and handle a customer call.

# Part 1: WxM Connector setup

The following video outlines the steps required to create the WxM connector. WxCC uses this connector to read the dispatches that are configured in WxM. This connector is also used to load the widgets into the agent desktop and FeedBack is triggered via the same.

<iframe width="560" height="315" src="https://www.youtube.com/embed/GI4nzVLLFCk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

* [Control hub](https://admin.webex.com)
* [WxM console](https://cx.cloudcherry.com)

## a) Identify the API key from WxM

* Login to the [WxM console](https://cx.cloudcherry.com)
* Enter the admin credentials.
* Dismiss informative alerts if any.
* Click on the User Profile (Top) icon and then Edit Profile
* Copy the API Key from the API Key section.
* If the API key is not present, click on Create and then copy the key.

## b) Configure WxM connector in Control hub

* Login to [Control Hub](https://admin.webex.com)
* Enter the Customer admin email id and the password.
* Navigate to **_Contact Center_** Card
* Click on **_Connectors_**
* Click on Set Up on Webex Experience Management card.
* Provide a unique identifier in the Name text area
* Provide the WxM admin Username
* Paste the API Key (copied above)
* Click on Save and then Close.

# Part 2: Onboarding CH Agent as WxM User

The following video demos how a Control Hub user is onboarded to WxM. We have to ensure that each of the agents in Control Hub is linked to one of the valid users in WxM. Based on the access of the WxM user, appropriate widgets will be loaded into Agent Desktop. Since the access control is based on the WxM user, this step is very critical.

<iframe width="560" height="315" src="https://www.youtube.com/embed/SmRBu4QFCos" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

* [Control hub](https://admin.webex.com)
* [WxM console](https://cx.cloudcherry.com)

## **IMPORTANT : Before You Begin**

* Please create a new agent in Control Hub with an email inbox to which you have access.
* The below steps will need you to activate a user and hence the request for an inbox to which you have access to click the user activation link.
* We will use this agent to login to Agent Desktop and handle voice calls, Email interaction, and Chat interaction.
* Hence ensure that the configured agent profile has required channels and is part of the voice, email & chat queue, and the respective Team

## a) Create WxM User and Generate API key

* Login to the [WxM console](https://cx.cloudcherry.com)
* Enter the admin credentials.
* Dismiss informative alerts if any.
* Navigate and click CX Setup by clicking the top left stacked 3 dots menu
* Click on Account Settings and then Users submenu
* Click on CREATE USER
* Input Display Name, Email, and Username.
* Scroll down and select Read & Write in USER TYPE.
* Click on Assigned Spaces and Check the 3 boxes to enable access to all 3 spaces.
* Click on CREATE and wait for the user creation confirmation dialog.
* Check the email inbox and click on the link in the email from Cisco Webex Experience Management support@xm.webex.com
* Set a password and confirm that you can login to WxM with these credentials.
* Note the username & password of the WxM agent which will be used to link the CH user with this WxM user.

## b) Identify Org ID, CH User ID and email of Agent

* Login to [Control Hub](https://admin.webex.com)
* Enter the Customer admin email id and the password.
* Click on Users
* Right-Click inside the browser and select the appropriate menu to open browser developer tools. If this is not possible, please use the browser menu option and open developer tools.
* open browsers developer tool's Network tab.
* Type in text Users into filter Urls by text.
* Now click on the newly added agent.
* Identify the URL which is of the form https://identity.webex.com/identity/scim/c0f66d1f-1a05-4843-bbb1-1ba5e19c233b/v1/Users/dee300db-5784-4bae-bae9-2f39d34f5ec0
* **Note that the text in the above URL will not match the one you find, as it's used just as an example
* From the URL the User id is the text after /Users/. Note this down.
* Alternatively, if you are proficient with browser dev tool debugging, you could just copy the bearer token of the above request and then run the same API in any of the REST clients and identify the User ID.
* Copy the email id of the agent and note it down.
* Close the browser dev tools.
* Now navigate to Account in Control Hub UI and copy the Organization ID and note it down.

## c) Run WxM OnBoard API

* Open any of the available REST clients. if you don't have a REST client installed on your laptop, please install the latest version of the postman.
* Open a new API request tab and select the HTTP method as POST.
* Input the URL as https://api.getcloudcherry.com/api/account/UpdateExternalIdp/Bulk
* Set the Authorization as Basic Auth and input the Username & Password of the WxM Agent that we created and activated above.
* In the Body section of the API request, paste the below:

```
{
   "ExternalIdentityProviderName":"webexci",
   "IDPMapppings":[
      {
         "ExternalUserId":"",
         "ExternalOrgId":"",
         "ExternalEmailId":""
      }
   ]
}
```

* Input the UserID, OrgID, and EmailID values which you have noted down from the above steps.
* Ensure that the API request Accept and Content-Type Headers are set to "application/JSON"
* Click the button to trigger the API request.

# Part 3: Enable WxM widgets in Desktop Layout

The following video demos how the Agent Desktop Layout JSON has to modify with the appropriate values of the WxM dashboard so that they are loaded into the widgets. The Space ID and the Metrics ID extracted from WxM decide which widget will be loaded for the agent. This lab section assumes that you are familiar with how the agent desktop layout can be modified and applied to a team.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Njie8PrB6Kk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Pre-requisites

* You are familiar with editing and updating desktop layout JSON
* You have the customer admin login credentials.

**Quick Links**

* [Control hub](https://admin.webex.com)
* [WxM console](https://cx.cloudcherry.com)

## a) Enable wxmConfigured flag

* Download the current layout of the team used by the newly created Agent.
* Edit the JSON file in an editor and search for the key wxmConfigured.
* If not changed already, change the value to true

## b) Enable Customer Experience Journey Widget

* Login to the [WxM console](https://cx.cloudcherry.com)
* Enter the admin credentials.
* Dismiss informative alerts if any.
* Navigate to the Customer Experience Journey response page.
* Click the Vertical Ellipsis on the right side of the screen and Export To Cisco Contact Center
* From the information pane, copy the Space Id and update this in the Customer Experience Journey section of the layout JSON.
* Since Customer Experience Journey, does not have metricsId you can use the space Id copied here as the metrics Id. Else you can the metrics Id of Customer Experience Analytics and paste it here (which you will get in the below steps)

## c) Enable Customer Experience Analytics Widget

* Login to the [WxM console](https://cx.cloudcherry.com)
* Enter the admin credentials.
* Dismiss informative alerts if any.
* Navigate to the Customer Experience Analytics Dashboard page.
* Click the Vertical Ellipsis on the right side of the screen and Export To Cisco Contact Center
* From the information pane, copy the Space Id and update this in the Customer Experience Analytics section of the layout JSON.
* From the information pane, copy the Metrics Id and update this in the Customer Experience Analytics section of the layout JSON.
* Save this JSON file and upload it in the appropriate layout used by the Test Agents Team.
* Now if you login as an agent and test Voice interactions, you will be able to access both the Customer Experience Analytics widget and Customer Experience Journey widget.

## d) Test Voice, Email and Chat Interaction

* Login to the recently created agent who has been OnBoarded in WxM.
* Trigger Voice, Email, and Chat interaction and confirm that both the WxM widgets are loaded on Agent Desktop and are visible.
* This confirms that our OnBoarding and the Json layout update is successful.

# Part 4: Configure Feedback node in Flow

The following video does a quick demo on how the FeedBack node should be implemented such that the caller receives an email with the survey link after completion of the call. The same steps can be followed to trigger an SMS with the survey link to the call ANI. Since Email and Chat are not integrated with Flow, Feedback cannot be used for those interactions. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/qGW6lRI7AA0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Pre-requisites

* You are familiar with creating and modifying flows
* You have a number from which you can make calls to the contact center.
* You have access to an inbox where the surveys can be posted.

**Quick Links**

* [Control hub](https://admin.webex.com)
* [WxM console](https://cx.cloudcherry.com)
* [WxCC Portal](https://portal.wxcc-us1.cisco.com/portal)

## a) Configure Feedback Node

* Login to portal with admin credential and navigate to `Routing Strategy`
* Click on `Flows` and edit the flow used in the call flow.
* Create 2 custom variables and hardcode values that will be used as `Customer ID` and `Email`.
* Navigate to `Event Flows` and insert `Feedback` node after `ContactEnded` event.
* Input `Activity Label` of your choice and select `Demo Email` from the `Dispatch` dropdown.
* Select `Set Language` to `English (US)` and select appropriate values for `Customer ID` and `Email`.
* For `Phone Number`, select the built-in flow variable `NewPhoneContact.ANI`
* Ensure that the `Feedback` nodes are connected properly with end nodes and `Validation` passes. Publish the change by clicking the `Publish Flow` button.

## b) Test Voice interaction and confirm that the survey is received by the caller's email

* Login to the recently created agent who has been OnBoarded in WXM.
* Trigger a voice call and ensure that the call connects to the agent and then terminate it.
* The survey link should be sent to the email specified in the flow custom variable.
* Click the link and fill the survey.

## c) Validate that the survey filled by the caller is recorded properly in WxM

* Login to the [WxM console](https://cx.cloudcherry.com)
* Enter the admin credentials.
* Dismiss informative alerts if any.
* Navigate to the `Overall Experience` dashboard and ensure that the feedback you provided is recorded in `WxM`

