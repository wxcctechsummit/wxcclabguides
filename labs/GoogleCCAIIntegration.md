---
title: "Lab 6: Google CCAI Integration"
---

# Table of Contents

- [1. Organization admin, setup google account](#1-organization-admin-setup-google-account)
- [2. Configure Google Connector in WxCC Control Hub](#2-configure-google-connector-in-wxcc-control-hub)
- [3. Configure Google Project](#3-configure-google-project)
- [4. Configure DialogFlow Agent](#4-configure-dialogflow-agent)
- [5. Validate Google Connector in WxCC Control Hub](#5-validate-google-connector-in-wxcc-control-hub)

# Introduction
<iframe width="560" height="315" src="https://www.youtube.com/embed/yto3w8pDrKs" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Lab Objective

This lab is designed to configure Google CCAI chat virtual agent to integrate in to WxCC.

End customer common queries can be answered by virtual agent before engaging agent.

## Pre-requisite

1. WxCC Portal url.
2. Admin login credentials to login to WxCC portal.
3. Google account along with login credentials.

# 1. Organization admin, setup google account

Customer/Partner should have an google account that can be used for creating new project in Google cloud.


# 2. Configure Google Connector in WxCC Control Hub

* login to control hub and select "Contact Center" tab.
* In Features, select "New" template for creating Chat Virtual agent.
* Choose Virtual Agent.
* Disable "Use for Voice" and leave it enabled "Use for chat", as we are going to configure virtual agent only for chat.
* Choose "Yes, I have a preconfigured Dialogflow agent" as I already have two pre-configured intents.
* Download the Intents and extract the "Intents" Zip folder, to view two intent json files. Those will be named as "escalation and handled" files.
* select "Dialogflow documentation" to download an authentication key as a JSON file from your Google Cloud Platform Service Account.

We will be able to see "Dialogflow CX and Dialogflow ES". CX will be used or suitable for large or very complex agents, whereas Dialogflow ES will be used or suitable for small and simple agent configurations.

* select Dialogflow ES and choose "Go TO THE DIALOGFLOW ES CONSOLE".


# 3. Configure Google Project

* Login to console.cloud.google.com
* Create new project and provide the project details.
* Search for "DialogFlow API" and select "Enable".
* Create "Service account" and grant "Dialogflow API admin" role.
* Create JSON key for newly created "Service account".
* Once created download the key and this is the key which will be used in WxCC Control Hub.


# 4. Configure DialogFlow Agent

* In "Dialogflow" window/tab, select "Create new agent". 
* Create a new agent which will be used for configuring Chat Virtual assistant, On left side of the dialogflow console, please select "+" sign.
* Provide the same name as earlier, "VirtualAssistant-Chat" and from the drop down choose newly created "Google Project".
* Select the three dots next to "CREATE INTENT" tab and opt for "Upload Intents" and choose the intent files "escalation and handled" one by one which were downloaded earlier from WxCC Control hub
* After uploading the intents, choose either of the one to verify the "Training Phrases" and "Responses".


# 5. Validate Google Connector in WxCC Control Hub

* Upload the JSON file i.e., "Upload Authentication Key" which was downloaded from "Google cloud project" in control hub.
* Validate the key after uploading and It should be successfully validated with out any errors.
* Provide the name for this "Google Virtual Assistant". Remember, this will be the name reflecting to end customers on chat interactions.
* Click Finish to save the configuration.

## DialogFlow Validation Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/SnxBo_gySIE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Avinash Satrasala (avsatras) | 05 Jan 2021 |
| 2.0 | Formatting changes | Mike Turnbow (miturnbo) | 20 Jan 2021 |
| 3.0 | Additional Video | Mike Turnbow (miturnbo) | 5 Feb 2021 |

