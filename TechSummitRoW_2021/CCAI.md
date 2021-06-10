---
title: "Lab 5: Google CCAI Integration"
---

### Overview of the lab:

In this Lab, we will go through the tasks that are required to setup **Contact Center AI with the Voice Bot and Text-to-Speech (TTS) capabilities**.

# Table of Contents

- [Introduction](#overview) 
  * [Lab Objective](#lab-objective)
  * [Pre-Requisites](#pre-requisites)
  * [Quick Links](#quick-links)
- [Part 1: Setup the Google Account](#1_setup_the_google_account)
- [Part 2: Setup Dialogflow Agent & Google Connector](#2_setup_dialogflow_google_connector)
- [Part 3: TTS, EWT & PIQ](#3_tts_etw_piq)

# Introduction

### Lab Objective

- This lab is designed to help you configure a Google DialogFlow Agent using CCAI (Contact Center AI) on Webex Contact Center and utilize TTS (Text-to-speech) capabilities.

- At the end of this lab, you should have a fully functioning bot front-ending the Webex Contact Center and text to speech prompts.

### Pre-requisites

- You must have a Google Account created.

- A credit/debit card (American Express, Mastercard or Visa) is needed to create the Google Billing account.
> **Note:** No card will be automatically billed anything, but a billing account needs to be setup to utilize TTS.

- Lab 2 (IVR Contact Routing Lab) should be completed, as same call flows will be used and expanded upon.


### Quick Links

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\

> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\

> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com/](https://desktop.wxcc-us1.cisco.com/){:target="_blank"}**

> Google Cloud Console: **[https://console.cloud.google.com/](https://console.cloud.google.com/){:target="_blank"}**

> Dialogflow: **[https://dialogflow.cloud.google.com/](https://dialogflow.cloud.google.com/){:target="_blank"}**



## Part 1: CCAI

### 1. Setup the Google Account

- Login to [Google Cloud Console](https://console.cloud.google.com/) with your Google Account credentials.

- Click on **Select a project** on top and then on **NEW PROJECT** on the pop-up window.

- Enter a name for your project, e.g. `TS2021-CCAI` and click on **CREATE**.

- Make sure you have this project selected. 

- On the navigation bar on the left, click on **Billing**.

- Click on **LINK A BILLING ACCOUNT** and then on **CREATE BILLING ACCOUNT**.

- Enter your Account Information (`Country`, `Mobile Phone`), accept the Terms of Service and click on **CONTINUE**.

- Enter your credit/debit card details and click on **START MY FREE TRIAL**. 

- Click on **CLOSE* on the next pop-up window.

- On the search bar, type `text to speech` and click on the **Cloud Text-to-Speech API**.

- Click on **ENABLE**.

- Click on **CREATE CREDENTIALS** on the top-right. 

- If prompted,choose **Cloud Text-to-Speech API** from the dropdown menu and check the **Application Data** option and **No, I'n not using them** and then click on **NEXT**.

- On the **Service account details**, enter a name for the service account, e.g. `TS2021_TTS_SA` and then click on **CREATE AND CONTINUE**. 

- On **Grant this service account access to project**, search and choose the **DialogFlow API Admin** role and then click on **CONTINUE** and then on **DONE**.

- Similarly, now on the search bar type type `dialogflow API` and click on the **Dialogflow API**.

- Click on **ENABLE**.

- Click on **CREATE CREDENTIALS** on the top-right. 

- If prompted,choose **Dialogflow API** from the dropdown menu and check the **Application Data** option and **No, I'n not using them** and then click on **NEXT**.

- On the **Service account details**, enter a name for the service account, e.g. `TS2021_CCAI_SA` and then click on **CREATE AND CONTINUE**. 

- On **Grant this service account access to project**, search and choose the **DialogFlow API Admin** role and then click on **CONTINUE** and then on **DONE**.

- To generate the required .json keys, click on the service account you created (e.g. **ts2021-ccai-sa@ts2021-ccai.iam.gserviceaccount.com**).

- Click on the **KEYS** tab and then on *ADD KEY** > **Create new key**.

- Choose the **JSON** key type and click on **CREATE**. Make sure you have the key saved locally.

- Click on **Service Accounts** ot the left and follow the same procedure to download the TTS JSON key as well.


### Part 2. Setup Dialogflow Agent & Google Connector

- Open [Control Hub Admin](https://admin.webex.com/) page.

- Go to **Contact Center** > **Connectors** and click **Set Up* on Google connector.

- Give a name to the connector, e.g. `techsummit_google_tts` and click on **Upload Authentication Key** to upload the .json file key downloaded before. Click on **Done**.

- Go to **Features** tab and click on **New** template.

- Click on **Virtual Agent**.

- Check only **Use For Voice** and click on **Next**.

- Choose **Yes, I have a preconfigured Dialogflow agent.**

- Click on **Download Intents** and save the .zip file with the two intents locally.

- Open a new tab and go to [Dialogflow page](https://dialogflow.cloud.google.com/) and login with your Google credentials.

- Click on **Create an Agent**.

- On the **GOOGLE PROJECT**, give a name to the agent,e.g. `TS_DF_Agent`,  choose the project created in the previous step and click on **CREATE**.

- On the next page, click on the dots on the top right (next to **CREATE INTENT**) and choose **Upload Intent**.

- Unzip the two intents you downloaded from Control Hub (**escalation.json** & **handled.json**) and upload it here.

- Go back to the Control Hub tab and click on **Next**.

- Give a name to your virtual agent, e.g. `TS_CCAI_Agent` and click on **Next**.

- Upload the CCAI/Dialogflow .json key downloaded in the previous part and click on **Validate**. If all is good, click on **Next**.

- Skip the avatar step and click **Next**.

- Click on **Finish** to complete the Virtual Agent creation.


### Part 3: TTS, EWT & PIQ

- Open Flow 3 in the Flow Designer from Lab 2 (IVR and Contact Routing).

- In the **Success** Play Message block, chose **Enable Text-to-Speech** under Prompt, choose your created connector (e.g. `techsummit_google_tts`) and set language as **en-GB-Standard-A**.

- Type `Thanks {{% raw %}} {{Customer_Name}} {{% endraw %}}, we got your information` as your TTS message.

- Make a new test call and verify that you get a personalized message with the customer's name based on the PIN provided.

- For **ETW**, after the **QueueContact1** node, add a **Get Queue info** block.

- Under *Queue Information**, select **Static Queue** and enter your queue.

- On success path, add a new **Play Message** block. Name it *EWT_PIQ**.

- Add the TTS connector to it similar to the step above and type `You Estimated Wait Time is {{% raw %}} {{GetQueueInfo.EWT}} {{% endraw %}} and your position in Queue is {{% raw %}} {{GetQueueInfo.PIQ}} {{% endraw %}}` as message.

- Similarly, for the **Insufficient Information** block, add a a new **Play Message** block and name it *PIQ**.

- Again, add the TTS connector and type `Your position in Queue is {{% raw %}} {{GetQueueInfo.PIQ}} {{% endraw %}}` as message.

- Save and publish the flow. Test the call flow and make sure you hear the PIQ prompt.

> **Note:** Make sure no agent is available to handle the call to be able to listen to the PIQ prompt.





### 2. Wire up the DialogFlow Agent inside of the Flow.

- In Flow Designer – Remove the menu block and the welcome message block. - We will use the CCAI Bot to front end the conversation, and then perform the lookup and send it to the queue.
- Put in the Virtual Agent block.
- For the Virtual Agent selection, select the CLUS_CCAI_Bot
- Make Prompts Interruptible for the bot.
- Under the Advanced settings, ensure that “Enable Conversation Transcript” is checked. This will help the agent get a copy of the conversation with the customer.
- Scroll down and configure the bot settings as detailed below

### 3. Configure the Settings for the Bot and the output connections

- The Bot has 2 connections – Handled and Escalated.
- Handled is meant to gracefully disconnect the call and end Self Service. - Connect the handled branch to a play message block with “Thank you for calling” using a TTS Play Message block.
- Escalated is meant to send the call to the queue. Send the caller to a Queued block by connecting the escalated Intent to the queued block.

### 4. Store the bot variables as CAD variables for the screen pop

- The bot block (VirtualAgent1) has 2 variables : LastIntent and TranscriptURL
- We will store these in CAD variables and pop them on the agent desktop.
- Create 2 CAD variables called lastIntent and transcriptURL
- Use the set variables as shown in the example above to set these as CAD variables.
- This will ensure that when the call hits the agent, the agent is able to view these statistics. It is also helpful during debugging.

### 5. Test the end to end flow

- Login to the agent desktop and go Idle (Not Ready)
- Call the main number on the entry point.
- You should hear the bot asks you what you want to do. (e.g “How may I help you”)

### 6. Experiment with what the configured Bot can do

> **Note:** This simple bot has been programmed on DialogFlow to give you information about the Cisco Live Session Schedule as well as escalate the call to an agent).

- Use any of the trigger intents to get information about the lab: “Cisco - - Live” “Tell me about your lab” “What labs are supported”
- Use any of the trigger intents to get to an agent: “I need Help” “I need an Agent” “Where is my proctor” “Help” “Assistance”, etc – these are the words that have utterances trained to trigger the escalation intent of the bot.
### 7. Have the Agent handle the call
- Have the agent go ready after you said “I need an agent”.
- The Agent should get the call, and be able to view the transcript on the agent desktop.







---

### **Congratulations! Google CCAI Integration lab is now complete!**

[Back to top](#table-of-contents)

---

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/TechSummitRoW_2021/HomePage.html";}
function nextLab() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/TechSummitRoW_2021/Analyzer.html";}
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
  padding: 10px;">Next Lab 6: Analyzer Lab</button>

</div>

