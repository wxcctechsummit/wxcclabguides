---
title: "Lab 7: Omnichannel Routing"
---

# Facebook Messenger Integration

## Table of Contents
- [1. Organization admin – set up facebook account](#1-organization-admin-\--set-up-facebook-account)
- [2. Configure Facebook Connector in WxCC Control Hub](#2-configure-facebook-connector-in-wxcc-control-hub)
- [3. Configure Facebook Entrypoint](#3-configure-facebook-entrypoint)
- [4. Configure Facebook Queue](#4-configure-facebook-queue)
- [5. Configure EntryPoint Mappings](#5-configure-entrypoint-mappings)
- [6. Entry point routing strategy creation](#6-entry-point-routing-strategy-creation)
- [7. Queue routing strategy creation](#7-queue-routing-strategy-creation)
  * [Testing Facebook Chat to Agent Desktop](#testing-facebook-chat-to-agent-desktop)
- [8. Agent Desktop: Contact offering to an Agent, Acceptance, and closure](#8-agent-desktop-contact-offering-to-an-agent-acceptance-and-closure)

## Introduction
<iframe width="560" height="315" src="https://www.youtube.com/embed/dibFEv-xv3g" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Lab Objective

This lab is designed to configure Facebook to integrate in to WxCC.

End customer can initiate queries from provided facebook page to contact center agents.

### Pre-requisite

1. WxCC Portal url.
2. Admin login credentials to login to WxCC portal.
3. Facebook account along with login credentials.
4. Agent account to login to agent desktop.


## 1. Organization admin – set up facebook account

* Customer/Partner should have an facebook account that can be used for creating new page.

* Login to the [Facebook](http://facebook.com/) to create a business page which will be used for your end customers.

* Once logged in, please select Pages tab which is on left side of the facebook home page.

* Now choose "Create New Page" which is on top left corner.

* Provide the information which is required for creating the page as per your business and organisation.

* Upload cover photo and Logo then save.


## 2. Configure Facebook Connector in WxCC Control Hub

* Login to the WxCC portal.

* Once logged into the portal, on left side menu expand to see the available tabs. Select Provisioning and launch users.

* Here we will be able to see the available users and option to launch control hub. Select "Cisco Webex Control Hub".

* login to control hub and select "Contact Center" tab.

* Please provide the same username which was used to login to Cisco WxCC portal.

* Once logged-in to control hub, please select "Contact Center" tab.

* Choose Connectors and select "Facebook Messenger"

* Provide Name and choose I do not have a Facebook Page ID and Access Token.

* Proceed with Authentication to get Page ID and Access Token.

* Once Authenticated copy Page ID and Access Token.

* Update these details in WxCC Hontrol Hub.

* Now you should be able to see the newly created Facebook Page in Social Channels.


## 3. Configure Facebook Entrypoint

* Login to the WxCC portal.

* Select left side menu, expand to see the available tabs. Select Provisioning and expand Entry Points/Queues, now choose Entry Point.

* Select "New Entry Point".

* Provide the Entry Point Name, Description and Channel type as "Social Channel" and Social Channel type as "Facebook Messenger" and save.


## 4. Configure Facebook Queue

* Select Provisioning and expand Entry Points/Queues, now choose Queue.

* Select "New Queue".

* Provide the Queue Name, Description and Channel type as "Social Channel".

* Now choose "Add Group" and select the required team names to whom these facebook contacts need to be routed.

* Update the Max time in queue and save.


## 5. Configure EntryPoint Mappings

* Select left side menu, expand Provisioning to see the available tabs. Select "Entry Point Mappings".

* Choose Social Messaging and select "New Mapping".

* Select the Connector and choose the one which we have created in Control Hub, then select entry point and save.  

## 6. Entry point routing strategy creation

* Select left side menu, expand to see the available tabs. Select "Routing Strategy"

* Choose newly created facebook Entrypoint.

* Select new Strategy, provide name, start & end date, add the newly create facebook queue then save.


## 7. Queue routing strategy creation

* Now from the routing strategy page, select the ‘queue’ that you created and choose ‘New Strategy’.

* Provide the Queue Name, start & end date, Max Time In Queue.

* 'Add Group' and Select the team to which the contact should be delivered and click save group.

* Now click save to complete Queue routing strategy settings. 

### Testing Facebook Chat to Agent Desktop
<iframe width="560" height="315" src="https://www.youtube.com/embed/6Y-VNupYLns" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## 8. Agent Desktop: Contact offering to an Agent, Acceptance, and closure

* Select left side menu in Wxcc Portal, expand to see the available tabs. Select "Agent Desktop".

* Login to agent desktop, provide agent login DN and choose the team.

* Once the agent goes Available, the facebook contact will be offered to the agent.

* Click "Accept" to handle the contact, after responding close the task.


Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Avinash Satrasala (avsatras) | 25 Jan 2021 |
| 2.0 | Final Release | Mike Turnbow (miturnbo) | 26 Jan 2021 |