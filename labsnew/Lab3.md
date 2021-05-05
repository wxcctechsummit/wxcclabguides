---
title: 'Lab 3: IVR and Contact Routing'
---

# Table of Contents

- [Part 1: Setup a Simple Flow and make a test call](#part-1-setup-a-simple-flow-and-make-a-test-call)
  - [1. Create the Voice Entry Point and Voice Queue](#3-create-an-inbound-voice-entry-point-and-voice-queue)
  - [2. Verify/Upload the Audio Prompts, Create the Entry Point Flow.](#4-verify-the-audio-prompts-create-the-entry-point-flow)
  - [3. Configure and Publish the Flow](#5-configure-and-publish-the-flow)
  - [4. Configure the Entry Point Routing Strategy](#6-configure-the-entry-point-routing-strategy)
- [Part 2: Adding Menu and Queue treatment to the call](#part-2-adding-menu-and-queue-treatment-to-the-call)
  - [1. Configure the Queue Treatment loop and Opt Out and Callback steps](#2-configure-the-queue-treatment-loop-and-opt-out-and-callback-steps)
  - [2. Point to the New flow in the Routing Strategy](#3-point-to-the-new-flow-in-the-routing-strategy)
  - [3. Test the end to end flow](#4-test-the-end-to-end-flow)
  - [4. Execute the Callback](#5-execute-the-callback)
- [Part 3: Configuring Outdial](#part-3-configuring-outdial)
  - [1. Verify/create the Outdial Entry Point and Queue](#1-verifycreate-the-outdial-entry-point-and-queue)
  - [2. Configure the Agent profile](#3-create-the-outdial-queue-routing-strategy)
  - [3. Create the Outdial Entry Point Routing Strategy](#2-create-the-outdial-entry-point-routing-strategy)
- [Part 4: HTTP Requests](#part-4-advanced-scripting-steps)
  - [1. Enhance the existing flow with an HTTP Request](#2-enhance-the-existing-flow-with-an-authentication-piece)
  - [2. Configure the Collect Digits block](#3-configure-the-collect-digits-block)
  - [3. Configure the custom variables and the HTTP Request Block](#3-configure-the-custom-variables-and-the-http-request-block)
  - [4. Configure the Conditional for Error Check](#4-configure-the-conditional-for-error-check)
  - [5. Point to the New flow in the Routing Strategy](#5-point-to-the-new-flow-in-the-routing-strategy)
  - [6. Verify the flow end to end](#6-verify-the-flow-end-to-end)
- [Part 5: Skills Based Routing](#part-4-advanced-scripting-steps)
  - [1. Configure the Skills and Skill Profiles](#1-copy-out-the-flow-and-configure-the-advanced-flow-2)
  - [2. Configure the Skills Based Queue](#2-enhance-the-existing-flow-with-an-authentication-piece)
  - [3. Configure the Agent with the Skill](#3-configure-the-collect-digits-block)
  - [4. Configure the Queue Block with SBR](#3-configure-the-custom-variables-and-the-http-request-block)

# Introduction

## Lab Objective

- This lab is designed to ensure you are able to configure a voice contact end to end and receive it on the agent desktop.

- The lab will also contain multiple exercises on flow designer to make you comfortable with the Webex Contact Center Flow Designer and the overall Contact Routing configuration.

- **IVR Prompts:** We will expect you to configure and upload static prompts shared for use below. You may also choose to use dynamic TTS prompts, it will not change the lab or its content. You can upload these "CiscoDemo" prompts and use them for the labs. You may also keep a copy of the zip file if you want to manually upload them. In the bonus lab sections, we also share how you can convert these prompts to dynamic TTS prompts using the Text to speech connector configuration available within flow designer.

> ### [Download the IVR Prompts - Static Prompts HERE](https://cisco.box.com/s/e6dgudpc3zru5urm31gcnqfcbebx79b9){:target="\_blank"}

- **Lookups, Advanced Scripting, Screen-pops:** We have chosen specific areas of focus for advanced scripting topics. We have more content shared in the bonus sections on how to get other use cases configured.

- **GoTo, ScreenPops, Skills Based Routing:** We will cover the newer features on Webex Contact Center, including the GoTo step, Screen Pop, and skills based routing.

# Lab Pre-requisites

> ## The Steps below summarize/recap Lab 1. Ensure you have Completed [Lab 1: Part 5 & 6 here](Lab1.md){:target="\_blank"}

> These tasks are to be completed by the customer administrator. By following these steps, you would have prepped the tenant to begin configuring different services offered by the platform. At the end of the lab, you should be able to login an agent with the configured user extension.

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="\_blank"}**\

> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="\_blank"}**\

> Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

**Check Licenses**

### 1. Login to Control Hub > Users.

- Ensure the agents have the contact center license selected and are properly configured as Contact center enabled on Webex Contact center.
- Ensure that they have activated the Email and are “Active” on Control Hub.

**Check Webex Calling Settings**

### 2. Verify Webex Calling Settings

- Check that a "Main" number is assigned to Webex Calling.
- Check that the Calling Location is correctly set to "Intelepeer"

**Synchronize Users**

### 3. Synchronize users to get any newly activated users.

- Got to Contact Center > Settings > Synchronize Users

**Check Admin settings, Agent Settings, Site, Team Configuration**

### 4. Launch Portal to ensure the admin user admin1pod**@** is Contact center configured for testing.

- A Site has already been created for the Admin: `Site_TS_`, `Team_TS`
- Ensure the Admin is Contact Center Enabled.
- Associate the User to the Site, Team, default Multimedia Profile - `Default_Telephony_Profile`.
- Verify by Launching the Agent Desktop and logging in.

> **Note:** Please Check the `Site_TS` that the user admin1pod__@email.carehybrid.com is assigned to. And create the `Team_TS` under the right Site.

- If you would like to Create a Team, create the Team under that Site - and assign the Team to the Agent.
- `Agent` > `Site` relationship cannot be changed. So all teams will need to be created under the same site.
- With the steps outlined in the previous lab and recap above, you should now be able to login to the agent desktop.

> Only teams that are in the same site of the Agent will be visible to assign to the agent.

Desktop URL: **https://desktop.wxcc-us1.cisco.com/**

### 5. Verify Webex Calling PC App Installation

> **Participants can download and install the WebEx Calling App for Agents, Admins or Supervisors and make on-net calls.**

**[Webex Calling PC APP - Download HERE !](https://cisco.app.box.com/s/fcbh0abcsruf5qxp99tj31ksx1bf2mh5){:target="\_blank"}**

**Download instructions**

**[https://help.webex.com/en-us/n730ah9/Install-the-Webex-Calling-App](https://help.webex.com/en-us/n730ah9/Install-the-Webex-Calling-App){:target="\_blank"}**\

> You will use the extension configured on Webex Calling : 3001 - to login to the Agent Desktop

| **User Role** | **Contents**                            | **Extension-DN Allotted** |
| ------------- | --------------------------------------- | ------------------------- |
| Admin         | admin1\_\<POD-ID\>@email.carehybrid.com | 3001                      |

### OPTIONAL : Creating More Users - Agents - Supervisors - For Test Calling INBOUND

- **Creating additional Agents OR Supervisors:** You may create additional aliases using Mailinator (3rd party email alias generator) **[https://www.mailinator.com/](https://www.mailinator.com/){:target="\_blank"}**\

- `These CAN be used for inbound call testing into the Contact Center : As Contact Center Customers!`

> Login to mailinator, create an inbox : `username@mailinator.com` will then be able to receive emails.

> Add the user to Control Hub Via > Control Hub > Users > Manage Users > Add via email : add the user_ID@mailinator.com

> Remember to `Click Synchronize Users` on Control Hub when adding new users!

## You are now ready to Begin the Lab!

---

# Part 1: Setup a Simple Flow and make a test call

> This lab is designed to help you to make an end to end test call into the contact center.

> The lab concludes with sending a test call from the caller (customer) to the agent desktop using a Simple Flow.

<iframe width="1024" height="576" src="https://www.youtube.com/embed/n_PiLTFcgZw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="\_blank"}**\

> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="\_blank"}**\

> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

### 1. Verify that your users are ready to login

> **Note:** Go to `Provisioning -> Users` to check the `Site` that the user is assigned to. And create the `Team` under the right `Site`.

- If you would like to Create a Team, create the `Team` under that `Site` - and assign the `Team` to the Agent.
- `Agent` > `Site` relationship cannot be changed. So all teams will need to be created under the same site.
- With the steps outlined in the previous lab and recap above, you should now be able to login to the **[Agent Desktop](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

> Only teams that are in the same site of the Agent will be visible to assign to the agent.

### 2. Verify your inbound numbers are correctly setup on Calling

- The inbound Numbers need to be added on Control Hub.
- The telephony option on the location needs to be set to Intelepeer.
- Settings page needs to have Intelepeer configured for subsequent locations created.

### 3. Create an inbound Voice Entry Point and Voice Queue

- Login to Portal and create an inbound voice entry point and voice queue. (Provisioning > Entry Point / Queue).

- Create the Entry Point named `EP_TS` where `<ID>` is your attendee ID provided.

- Create the Queue named `Q_TS` where `<ID>` is your attendee ID provided.

**Here are the Queue Settings**

| Configuration                       | field Value             |
| ----------------------------------- | ----------------------- |
| Name                                | Q_TS                    |
| Channel Type                        | Telephony               |
| _---- Contact Routing Settings ---_ |
| Queue Routing Type                  | Longest Available Agent |
| Call Distribution                   | `<Add team>`            |
| _---- Advanced Settings ---_        |
| Service Level Threshold             | 60                      |
| Maximum Time in Queue               | 600                     |
| Time Zone                           | Default                 |

- `<ID>` is your attendee ID provided.

---

- Map the DN from Control Hub - that is assigned to Wx Calling - on the Entry Point Mappings page. (Proivisioning > Entry Point Mappings). Map the DN to EP_voice_TS

### 4. Verify the Audio Prompts, Create the Entry Point flow.

- The audio prompts required for the script build out are wav files. The whole bundle of [wav files can be found here](https://cisco.box.com/s/oakd708czpfe0cpcgc3fd08o7ulxd9hw){:target="\_blank"} **But these are already uploaded for you**.

> **Note:** Uploaded audio files are already under > Routing Strategy (from Portal) > Resources > Audio Files.

### 5. Configure and Publish the flow

- Configure the flow `flow_Lab1_Task1<ID>` with a Play prompt - welcome message and Disconnect
- Configure the flow `flow_Lab1_Task2<ID>` with a Play prompt - welcome message and queue block and play music block.
- Configure the Queue Block to `Queue_LAA_<ID>`. Map the queue inside of the q ueue block.
- Configure the play music to loop, and start 0, end 10 to play 10 seconds of music.
- Verify and publish the flow.

* Note: `<ID>` is your attendee ID provided.

### 6. Configure the Entry Point Routing Strategy

- Configure the Open 24x7 routing strategy time of day on the Entry Point Routing strategy by selecting it on the Routing Strategies >`EntryPoint_CL_Lab_<ID>`.
- Map the flow flow_wxcclab you just created in there.

### 7. OPTIONAL Download and Login in the Webex Calling app for mobile

> **Note:** If you are outside the US, you need two Webex Calling app for placing a call to Entry Point and accepting on the agent side. In this lab, we will use the Webex Calling app for mobile for **supervisor** account.

- Open the Application Manager (**Play Store** or **App Store**) on your mobile phone.

- Search for **_webex calling_**.

- **Download** and **Open** the app. Click `Get Started`.

- Login in the app by selecting **_Region_** as **North America**.

- Login using **_Email address_** `supervisor_<ID>@mailinator.com` and same **_Password_** as the admin account.

> **Note:** Make sure that you give access to the phone's microphone for the calling app.

![WxCallingAndroid](https://wxcctechsummit.github.io/holcct2100/images/wxcallingandroid.png)

### 8. Make a test call

- Login to the agent desktop into `Team_wxcclab` and go to a ready state.

- Task 1 > Call the Dial number > Hear the welcome prompt and call should get disconnected.
- Task 2 > Call the Dial number > Available agent gets connected immediately, If the Agent is not available the call is queued and music is played.

---

## Congratulations! You're done with Part 1!

## You are ready to start Part 2!

# Part 2: Adding Menu and Queue treatment to the call

> This lab is designed to help you configure a Menu step in the call flow along with Queue Treatment. We will also configure counters and Opt-outs within the queue, along with Callbacks.

> At the end of this lab, you should be able to hear the Menu prompt, and Opt-out of queue settings in the flow, and send a courtesy callback call to the customer by picking a ready agent.

<iframe width="1024" height="576" src="https://www.youtube.com/embed/BKid4Q--dp0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="\_blank"}**\

> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="\_blank"}**\

> Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

## Steps

### 1. Copy out the flow and configure the advanced flow

- Open the Portal > Routing Strategy > Flow page.
- Copy the existing flow flow_Lab1_Task2 and edit the copied flow - name it `Flow2`
- Edit the flow to go into flow designer.
- Ensure that you configure the Menu steps with a 3 option - 2 queue, 1 Blind Transfer step.
- Ensure you configure all the fields in the menu step including the prompts and the entry timeout (requires you to explore all options on the step).
- Ensure you configure all the blind transfer location to Cisco Toll Free : `+18005536387`
  **Note: This will actually connect you to the live toll free number!**

> **Important TIP on the MENU Block**

> `Make all Menu Steps Interruptible by default` - This gives callers an option to bypass the prompt. It is a small checkbox on the Menu Step.

> `In the Menu Block > Advanced Settings > Entry Timeout = Make it 10 Seconds` - This gives callers enough time to complete the DTMF (digit) entry.

---

> You can Skip to 08:00 in the Video to Start Building the Flow Out by following the video

### 3. Configure the Queue Treatment loop and Opt Out and Callback steps

- In Flow Designer - Configure the Queue treatment for the first queue. Use the queueCounter variable and configure the Opt out steps including the high volume message and the callback step.
- Configure the voicemail destination to the same external number above.
  Validate the flow and publish it.

### 4. Plug In New Flow into Routing Strategy

- Go to the routing Strategy page > Routing Strategy > `EntryPoint_wxcclab_<ID>`
- Once the flow is published, configure the Entry Point Routing strategy to point to the new flow `Flow_Lab2_<ID>`

### 5. Test the end to end flow

- Login to the agent desktop and go Idle (Not Ready)
- Test Queue treatment by going not ready on the agent desktop.
- Call the main number on the entry point and go into the queue. You should hear the queue twice and then have an option to leave a callback.
- leave the callback and the call should end.

### 6. Execute the Callback

- Have the agent go ready after you left a callback.
- They should receive the callback call.

---

## Congratulations! You're done with Part 2!

## You are ready to start Part 3!

# Part 3: Configuring Outdial

> This lab is designed to complete configuring the outdial capability on the Agent Desktop.

> At the end of the lab, your agent will be able to make an outbound call from the Agent Desktop.

<iframe width="1024" height="576" src="https://www.youtube.com/embed/NMu9goAQJQ0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="\_blank"}**\

> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="\_blank"}**\

> Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

## Steps

### 1. Verify/create the Outdial Entry Point and Queue

- Login to Portal > Provisioning > Outdial Entry Point > Configure an Outdial Entry Point.
- Verify you already have an outdial Queue configured on Portal > Provisioning > Outdial Queue.
- Ensure that the system created outdial entry points and queues are present and configure their settings.
- Alternatively, you can setup a new Outdial Entry Point as shown in the video.

### 2. Create the Outdial Entry Point Routing Strategy

- Go Routing Strategy > Outdial Entry Point-1 OR the One you just setup
- Configure the outdial entry point routing strategy to the script Outdial_EP.js which is the system default.
- Ensure the strategy time of day setting is correctly open 24x7 and marked default.

> **Note:** There are no more Queue Routing Strategies on the new Webex Contact Center.

### 3. Setup Your Agent Profile for Outdial

- Go to Provisioning > Agent Profiles > Select the Agent Profile and go to the Dial Plan tab.
- Configure all the Outdial settings on the dial plan as shown in the video.
- Attach the Outdial ANI, Address books etc. to the agent profile. Setup the Dial Plan Settings.

### 4. Test Outdial

- Logout/login the Agent on the agent desktop for the new agent profile settings to take effect.
- You should see the Outdial button and the agent is now able to make an outdial call.
- Test it by calling your cell or the provided Cisco Public Tollfree - `+18005536387` –Note: This will actually connect you to a live toll free number for Cisco Support!
- You should have all the connected call features pop on the agent desktop once the call is complete.

---

## Congratulations! You're All done with the Part 3! Now onto Part 4!

---

# Part 4: Advanced Scripting Steps - HTTP Request

<iframe width="1024" height="576" src="https://www.youtube.com/embed/gXhVTkGazmk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="\_blank"}**\

> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="\_blank"}**\

> Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

## Steps

### 1. Copy out the flow and configure the advanced flow 2

- Open the Portal > Routing Strategy > Flow page.
- Copy the existing flow `Flow2` and edit the copied flow - name it `Flow3`
- Edit the flow to go into flow designer.

### 2. Enhance the existing flow with an authentication piece

- Drag a play message block, Collect Digits, HTTP Request, Condition Block, 2 more Play message blocks and put them in front of the menu step.
- Ensure the prompts are plugged in to the play message prompts. `welcome`, `enter_pin`, and after the HTTP and Condition, a corresponding success and failure prompt.

> **Important TIP on the MENU Block**

> `Make all Menu Steps Interruptible by default` - This gives callers an option to bypass the prompt. It is a small checkbox on the Menu Step.

> `In the Menu Block > Advanced Settings > Entry Timeout = Make it 10 Seconds` - This gives callers enough time to complete the DTMF (digit) entry.

### 3. Configure the Collect Digits block

- Configure the Collect Digits Block to a 5 digits max/min and ensure the timeouts are properly setup.

### 4. Configure the custom variables and the HTTP Request Block

- Create 3 Custom variables - mark them CAD variables - with names `customer_Name`,`customer_Email` ,`customer_Account` with labels `Name`, `Email`, `Account` and values of `Unavailable` OR `null` - _(depends on what you prefer as the default for the agents to see if no info is available in the data dip)_

> The request we will construct is :

**HTTPS GET -> https://5f97898842706e0016957443.mockapi.io/crm/api/customers?pin=18716**

- Use the variable from the CollectDigits1.EnteredPIN variable to inject it in the pin lookup.
- We will construct it as follows

```
HTTP Request
GET https://5f97898842706e0016957443.mockapi.io/crm/api/customers

Query Parameters:
pin with {{CollectDigits.DigitsEntered}}

with value of the block (recheck your block variable name!)

The type would be application/json

The Parse settings would be :
customerName = $.[0].name
customerEmail = $.[0].email
customerPhone = $.[0].phone
```

**Tech-Tip:** Here are some practice exercises you can try by going to jsonpath.com

> - Go to https://5f97898842706e0016957443.mockapi.io/crm/api/customers

> - Copy out the JSON into https://jsonpath.com on the left pane.

> - Try out all of these to learn how JSON path works!

| Query For                                                     | Parse statement                       |
| ------------------------------------------------------------- | ------------------------------------- |
| All Customers                                                 | `$.*`                                 |
| First Customer                                                | `$.[0]`                               |
| Last Customer                                                 | `$.[-1:]`                             |
| First two customers                                           | `$.[0:2]`                             |
| Last two customers                                            | `$.[-2:]`                             |
| Second from last                                              | `$.[-2:-1]`                           |
| All the names                                                 | `$..name`                             |
| All the pins                                                  | `$..pin`                              |
| All the customers who’s pin value is more than 70000 or 80000 | `$..[?(@.pin > 70000)]`               |
| All details of customer with account number                   | `$..[?(@.account == "87305901”)].*`   |
| Name of customer with account number                          | `$.[?(@.account == "70579265")].name` |

### 5. Configure the Conditional for Error Check

- Use the httpBlock.StatusCode variable to check the value retured.
- Note that the test API does not give a 404 but an empty list [] with a 200 when no match is found. However, this step is just to understand error handling and checking.
- Use the `</>` expression check on the condition and play success and failure prompts accordingly.
- Ensure all the settings per block are entered and properly setup.
- Validate and Publish the new script, correcting any errors that show up during validation.

### 6. Point to the New flow in the Routing Strategy

- Go to the routing Strategy page > Routing Strategy > `EP_wxcclab_<ID>`
- Once the flow is published, configure the Entry Point Routing strategy to point to the new flow `Flow_Lab3_<ID>`.

### 7. Verify the flow end to end

- Verify the new flow end to end by first, logging into the Agent Desktop and going into a ready state.

Execute the Test:

- Call the Dial number > Enter the 5 digit PIN number > On Main Menu press 2 > call gets connected to agent,

`Agent should see all CAD variables (Customer Name, Email, Account Number)`

---

## Congratulations! You're done with Part 4!

## You are ready to start Part 5!

---

# Part 5: Skills Based Routing - PIQ

<iframe width="1024" height="576" src="https://www.youtube.com/embed/b-KyHUia-Bk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="\_blank"}**\

> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="\_blank"}**\

> Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

## Steps

### 1.Create Skill Definition

- Open portal > Provisioning > Skill > Skill Definition
- Click (New Skill Creation) > Give Name(Agent_Profiency)and Description(Agent_Profiency) Type > `Proficiency`
- Click (New Skill Creation) > Give Name(Premium_Agent)and Description(Premium_Agent) Type > `Text`

> **Note:** We are using "TEXT Skills" in this SBR lab so that you can directly target agents with a specific variable from flow. This gives powerful capabilities as you will see later.

### 2.Crete Skill Profile

- Open portal > Provisioning > Skill > skill Profile
- Click (New Skill Profile) > Give Name - `Cisco_Live_SP1` and Description - `Cisco_Live_SP1` Select only `Agent_Proficiency` enter Skill Value to `5`
- Click (New Skill Profile) > Give Name - `Cisco_Live_SP2` and Description - `Cisco_Live_SP2` Select `Agent_Proficiency` enter Skill Value to `5` and `Premium_Agent` and enter `Skill Value` to `Yes`

### 3. Add skill profile to User/ Agent

- Open portal > Users
- Edit user > under Skill Profile select the skill profile created in step 2 - `Cisco_Live_SP2`

### 4.Create new Queue with Skill based routing and Add team

- Open portal > Provisioning > Entry point/Queue > Queue
- Create new Queue > Give Name and Description
- Channel Type > Telephony
- Queue Routing Type > Skill Based > Best Available Agent
  Add Team > Team[Team_wxcclab]

| Configuration field        | Value                |
| -------------------------- | -------------------- |
| Name                       | Queue_SBR            |
| Channel Type               | Telephony            |
| _Contact Routing Settings_ |
| Queue Routing Type         | Skills Based         |
| Agent Selection            | Best Available Agent |
| Call Distribution          | `<Add team>`         |
| Service Level Threshold    | 20                   |
| Maximum Time in Queue      | 7200                 |
| Time Zone                  | Default              |

### 5. Change the previous flow with Skill based routing queue

- Open the Flow created before and click on Queue Contact node (Team1) and change the queue from Queue_Dummy to Queue_SBR
- Skill Requirement Details > Select Skill and condition
  Under value – Skill Requirements

**Set the following settings**

> `Agent_Proficiency >= 4`

> `Premium_Agent` IS {% raw %}{{premium_cust_set}}{% endraw %}

> Enable Skill Relaxation After waiting in queue for: `15 seconds`

**Set skill requirements to:**

> `Agent_Proficiency >= 4`

### 6. Additional String Manipulation ! - CUSTOMER EMAIL CHECK

- Create Custom String variable, `Cust_Premium_check` and `Cust_Premium_set`.
- Drag and Drop Set Variable, Condition node and another Set Variable as explained in Video

- In the First set variable parse for email, use

{% raw %}
\'\'\'{{ Customer_Email \| split(\"@\") \| last }}\'\'\'
{% endraw %}

to parse the domain name of email

> **Note:** We used "" within the String hence we will need a new String wrapper of `'''String with "substring" to differentiate'''`

> The filter functions on Pebble templates has a lot of info.

> [See Pebble Split Function](https://pebbletemplates.io/wiki/filter/split/){:target="\_blank"}

> [See Pebble Last Filter](https://pebbletemplates.io/wiki/filter/last/){:target="\_blank"}

> In the Condition node, use this condition

{% raw %}
{{Cust_premium_check =="gmail.com"}}
{% endraw %}

- If `True`, Set `Cust_premium_check` to `Yes` and connect it to main menu
- If `False`, connect it to main menu

### 7. PIQ and EWT - Position in Queue and Estimated Wait Time for the caller

- Drag and drop Queueinfo node after “Team2 Queue Contact node” play EWT and PIQ from the success link.
- Play PIQ alone from the “Insufficient Information ” link .
- Connect the Failure link to the Play Music node.

### 8. Make a call and Test the end to end flow

- Verify the new flow end to end by first, logging into the Agent Desktop and going into a ready state.
- Call the Dial number > Enter 5 digit pin non premium agent ( `36238` ) > On - Main Menu press 1 > Call queued for 15 seconds and gets connected to agent
- Call the Dial number > Enter 5 digit pin premium agent ( `93752` ) > On Main Menu press 1 > Call gets connected to agent immediately

---

## Congratulations! You're done!

Changelog:

| **Version** | **Comments**     | **Author**\                      | **Date**      |
| ----------- | ---------------- | -------------------------------- | ------------- |
| 1.0         | Initial Release  | Arunabh Bhattacharjee (arubhatt) | 10 Jan 2021   |
| 1.1         | Updated with SBR | Arunabh Bhattacharjee (arubhatt) | 25 April 2021 |

---

<div id="button-row">
	<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go back to Main Page</button>

<!--

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Next Lab 3: IVR and Contact Routing</button>
-->
</div>

<script>
function mainPage() {
  window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LabLibrarynew";
  }
</script>
