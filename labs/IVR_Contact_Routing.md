---
title: "Lab 2: IVR and Contact Routing"
---

**Overview of the lab**

<iframe width="560" height="315" src="https://www.youtube.com/embed/cyPxPKncOhM" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents
- [Part 1: Setup a Simple Flow and make a test call](#part-1-setup-a-simple-flow-and-make-a-test-call)
  * [1. Verify that your users are ready to login](#1-verify-that-your-users-are-ready-to-login)
  * [2. Verify your inbound numbers are correctly setup on Calling](#2-verify-your-inbound-numbers-are-correctly-setup-on-calling)
  * [3. Create an inbound Voice Entry Point and Voice Queue](#3-create-an-inbound-voice-entry-point-and-voice-queue)
  * [4. Verify the Audio Prompts, Create the Entry Point flow.](#4-verify-the-audio-prompts-create-the-entry-point-flow)
  * [5. Configure and Publish the flow](#5-configure-and-publish-the-flow)
  * [6. Configure the Entry Point Routing Strategy](#6-configure-the-entry-point-routing-strategy)
  * [7. Configure the Queue Routing Strategy](#7-configure-the-queue-routing-strategy)
  * [8. Make a test call](#8-make-a-test-call)
- [Part 2: Adding Menu and Queue treatment to the call](#part-2-adding-menu-and-queue-treatment-to-the-call)
  * [1. Copy out the flow and configure the advanced flow](#1-copy-out-the-flow-and-configure-the-advanced-flow)
  * [2. Configure the Queue Treatment loop and Opt Out and Callback steps](#2-configure-the-queue-treatment-loop-and-opt-out-and-callback-steps)
  * [3. Point to the New flow in the Routing Strategy](#3-point-to-the-new-flow-in-the-routing-strategy)
  * [4. Test the end to end flow](#4-test-the-end-to-end-flow)
  * [5. Execute the Callback](#5-execute-the-callback)
- [Part 3: Configuring Outdial](#part-3-configuring-outdial)
  * [1. Verify/create the Outdial Entry Point and Queue](#1-verifycreate-the-outdial-entry-point-and-queue)
  * [2. Create the Outdial Entry Point Routing Strategy](#2-create-the-outdial-entry-point-routing-strategy)
  * [3. Create the Outdial Queue Routing Strategy](#3-create-the-outdial-queue-routing-strategy)
  * [4. Test Outdial](#4-test-outdial)
- [Part 4: Advanced Scripting Steps](#part-4-advanced-scripting-steps)
  * [1. Copy out the flow and configure the advanced flow 2](#1-copy-out-the-flow-and-configure-the-advanced-flow-2)
  * [2. Enhance the existing flow with an authentication piece](#2-enhance-the-existing-flow-with-an-authentication-piece)
  * [3. Configure the Collect Digits block](#3-configure-the-collect-digits-block)
  * [3. Configure the custom variables and the HTTP Request Block](#3-configure-the-custom-variables-and-the-http-request-block)
  * [4. Configure the Conditional for Error Check](#4-configure-the-conditional-for-error-check)
  * [5. Point to the New flow in the Routing Strategy](#5-point-to-the-new-flow-in-the-routing-strategy)
  * [6. Verify the flow end to end](#6-verify-the-flow-end-to-end)


# Introduction

## Lab Objective

- This lab is designed to ensure you are able to configure a voice contact end to end and receive it on the agent desktop.

- The lab will also contain multiple exercises on flow designer to make you comfortable with the Webex Contact Center Flow Designer and the overall Contact Routing configuration.

**IVR Prompts:** We will be configuring static prompts for you and pre-uploading them in part 1. You may also keep a copy of the zip file if you want to manually upload them. In the bonus lab, we also share how you can convert these prompts to dynamic TTS prompts using the Text to speech connector configuration available within flow control.  

**Lookups, Advanced Scripting, Screen-pops:** We have chosen specific areas of focus for advanced scripting topics. We have more content shared in the bonus sections on how to get other use cases configured.

## Pre-requisite

Before you begin this lab
>The following video outlines the pre-requisites before beginning the lab.

<iframe width="560" height="315" src="https://www.youtube.com/embed/hO-yCjjLA5o" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

1. Setup Webex Contact Center Button is Clicked and Greyed Out.
2. Users are provisioned on Control hub.
3. Users configured on Control Hub and assigned Licenses.
4. Admins have proper Webex Contact Center license.
5. Synchronize users is clicked.
6. All users visible on Portal > Users and Contact Center Enabled.
7. All Users that need to login to agent desktop are assigned `Site_wxcclab` and `Team_wxcclab` - e.g agent1,super1,agent2,super2,etc. Also All agents are properly assigned Agent Profiles and Multimedia profiles.
8. Control Hub, Portal and Agent Desktop URLs handy.
9. Admin credentials handy for configuration.
10. Agent Credentials handy to Handle contacts.
11. External Number to Route Transfer outs, voice mail within flow : **Cisco Support Helpline -- `+18005536387`**  -- P.S: *This will actually connect you to the live toll free number!*

**Note on Above Prerequisite Configuration**
> Login to `Control Hub` > Users.
- Ensure the agents have the contact center license selected and are properly configured as Contact center enabled on Webex Contact center. 
- Ensure that they have activated the Email and are "Active" on Control Hub. Synchronize users to get any newly activated users.

> Launch Portal to ensure all the users (admins, agents, supervisors) are contact center configured for testing.
- Create a Site : `Site_wxcclab`, `Team_wxcclab`
- Activate the agents to be Contact Center Enabled.
- Associate the Agents to the Site, Team, default Multimedia Profile - `Default_Telephony_Profile`.
- Verify by Launching the Agent Desktop and logging in.

> Participants can choose to download and install the WebEx Calling App for Agents, Admins or Supervisors and make on-net calls.

**Download instructions**

**[https://help.webex.com/en-us/n730ah9/Install-the-Webex-Calling-App](https://help.webex.com/en-us/n730ah9/Install-the-Webex-Calling-App)**

**Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com)**

> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal)**

> Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com)**


## Part 1: Setup a Simple Flow and make a test call

<iframe width="560" height="315" src="https://www.youtube.com/embed/52YiWRZJVcM" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com)**

> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal)**

> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com)**


### 1. Verify that your users are ready to login
- With the steps outlined in the previous lab and recap above, you should now be able to login to the agent desktop.

### 2. Verify your inbound numbers are correctly setup on Calling 
- The inbound Numbers need to be added on Control Hub.
- The telephony option on the location needs to be set to Intelepeer.
- Settings page needs to have Intelepeer configured for subsequent locations created.

### 3. Create an inbound Voice Entry Point and Voice Queue
- Login to Portal and create an inbound voice entry point and voice queue. (Provisioning > Entry Point / Queue). Create `EP_voice_wxcclab` and `Q_voice_wxcclab` respectively.
- Map the DN from Control Hub - that is assigned to Wx Calling - on the Entry Point Mappings page. (Proivisioning > Entry Point Mappings). Map the DN to `EP_voice_wxcclab`

### 4. Verify the Audio Prompts, Create the Entry Point flow.
- The audio prompts required for the script build out are wav files. The whole bundle of wav files [can be found here](/labs/prompts). Right click > Save link as OR click and then hit download.
- You may listen to the files to get an idea of the kind of flows being constructed in the later labs.
- To create a flow and have these wav files ready for use, ensure that these prompt files are already uploaded to the org.
- To upload the audio files, Go to  Routing Strategy (from Portal) > Resources > Audio Files and ensure that the audio files are uploaded. (Browse > New > Upload the files)
- Then, you can go to flow to create the flow. Routing Strategy (from Portal) > Flow > New and create the new flow as described in the video above.

### 5. Configure and Publish the flow
- Configure the flow `flow_wxcclab` with a Play prompt - welcome message and queue block and play music block.
- Configure the Queue Block to `Q_voice_wxcclab`. Map the queue inside of the queue block.
- Configure the event flow under the queue - ensure they have end flow steps.
- Configure the play music to loop, and start 0, end 120 to play 2 minutes of music.
- Verify and publish the flow.

### 6. Configure the Entry Point Routing Strategy
- Configure the Open 24x7 routing strategy time of day on the Entry Point Routing strategy by selecting it on the Routing Strategies > `EP_voice_wxcclab`.
- Map the flow `flow_wxcclab` you just created in there.

### 7. Configure the Queue Routing Strategy
- Create the Queue routing strategy for `Q_voice_wxcclab` using a 24x7 open queue.
- Map the Team `Team_wxcclab` to the Queue. Your Agent will then login to that team to get the call.

### 8. Make a test call
- Login to the agent desktop into `Team_wxcclab` and go to a ready state.
- Dial the number using your cell. You should hear the welcome prompt and get the call on the agent desktop.

## Part 2: Adding Menu and Queue treatment to the call


<iframe width="560" height="315" src="https://www.youtube.com/embed/6KrtAJuX_J0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com)**

> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal)**

> Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com)**

### 1. Copy out the flow and configure the advanced flow
- Open the Portal > Routing Strategy > Flow page.
- Copy the existing flow `flow_wxcclab` and edit the copied flow - name it `advanced_flow1_wxcclab`
- Edit the flow to go into flow designer. 
- Ensure that you configure the Menu steps with a 3 option - 2 queue, 1 Blind Transfer step.
- Ensure you configure all the fields in the menu step including the prompts and the entry timeout (requires you to explore all options on the step).
- Ensure you configure all the blind transfer location to Cisco Toll Free :  `+18005536387` --Note: *This will actually connect you to the live toll free number!*

### 2. Configure the Queue Treatment loop and Opt Out and Callback steps
- In Flow Designer - Configure the Queue treatment for the first queue. Use the `queueCounter` variable and configure the Opt out steps including the high volume message and the callback step.
- Configure the voicemail destination to the same external number above.
- Validate the flow and publish it.

### 3. Point to the New flow in the Routing Strategy
- Go to the routing Strategy page > Routing Strategy > `EP_voice_wxcclab`
- Once the flow is published, configure the Entry Point Routing strategy to point to the new flow `advanced_flow1_wxcclab`.

### 4. Test the end to end flow
- Login to the agent desktop and go Idle (Not Ready)
- Test Queue treatment by going not ready on the agent desktop.
- Call the main number on the entry point and go into the queue. You should hear the queue twice and then have an option to leave a callback.
- leave the callback and the call should end.

### 5. Execute the Callback
- Have the agent go ready after you left a callback.
- They should receive the callback call.

## Part 3: Configuring Outdial

<iframe width="560" height="315" src="https://www.youtube.com/embed/UMUM3zJUK7c" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com)**

> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal)**

> Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com)**


### 1. Verify/create the Outdial Entry Point and Queue
- Login to Portal > Provisioning > Outdial Entry Point / Outdial Queue.
- Ensure that the system created outdial entry points and queues are present and configure their settings.
- Go to Provisioning > Outdial ANI > Create an Outdial ANI on the setup by mapping it to your existing toll free.
- Go to Provisioning > Agent Profiles > Select the Agent Profile and go to the Dial Plan tab.
- Configure all the Outdial settings on the dial plan.


### 2. Create the Outdial Entry Point Routing Strategy
- Go Routing Strategy > Outdial Entry Point-1 and configure the outdial entry point routing strategy to the script `Outdial_EP.js` which is the system default.
- Ensure the strategy time of day setting is correctly open 24x7 and marked default.

### 3. Create the Outdial Queue Routing Strategy
- Go Routing Strategy > Outdial Queue-1 and configure the outdial queue routing strategy to map to the `Team_wxcclab`.

### 4. Test Outdial
- Logout/login the Agent on the agent desktop for the new agent profile settings to take effect.
- You should see the Outdial button and the agent is now able to make an outdial call.
- Test it by calling your cell or the provided Cisco Public Tollfree -  +18005536387` --Note: *This will actually connect you to the live toll free number!*
- You should have all the connected call features pop on the agent desktop once the call is complete.

## Part 4: Advanced Scripting Steps

<iframe width="560" height="315" src="https://www.youtube.com/embed/9_c_smmWGZA" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com)**

> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal)**

> Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com)**

### 1. Copy out the flow and configure the advanced flow 2
- Open the Portal > Routing Strategy > Flow page.
- Copy the existing flow `advanced_flow1_wxcclab` and edit the copied flow - name it `advanced_flow2_wxcclab`
- Edit the flow to go into flow designer.

### 2. Enhance the existing flow with an authentication piece
- Drag a play message block, Collect Digits, HTTP Request, Condition Block, 2 more Play message blocks and put them in front of the menu step.
- Ensure the prompts are plugged in to the play message prompts.
`welcome`, `enter_pin`, and after the HTTP and Condition, a corresponding `success` and `failure` prompt.

### 3. Configure the Collect Digits block
- Configure the Collect Digits Block to a 5 digits max/min and ensure the timeouts are properly setup.

### 3. Configure the custom variables and the HTTP Request Block
- Create 3 Custom variables - mark them CAD variables - with names `customerName`,`customerEmail` ,`customerAccount` with labels `Name`, `Email`, `Account` and values of `None` OR `Unavailable` OR `null` - (depends on what you prefer as the default for the agents to see if no info is available in the data dip)
- The request we will construct is : HTTPS GET -> https://5f97898842706e0016957443.mockapi.io/crm/api/customers?pin=18716
- Use the variable from the `CollectDigits1.EnteredPIN` variable to inject it in the pin lookup.
- We will construct it as follows

The HTTP Request URL : https://5f97898842706e0016957443.mockapi.io/crm/api/customers.

Query Parameters: 

`pin` with 
value of the block {{`CollectDigits1.EnteredPIN`}}

(recheck your block variable name!)

The type would be `application/json`

The Parse settings would be :

`customerName` with `$.[0].name`

`customerEmail` with `$.[0].email`

`customerPhone` with `$.[0].phone`

**Tech-Tip:** Here are some practice exercises you can try by going to jsonpath.com

- Go to [https://5f97898842706e0016957443.mockapi.io/crm/api/customers](https://5f97898842706e0016957443.mockapi.io/crm/api/customers)
- Copy out the JSON into [https://jsonpath.com](https://jsonpath.com) on the left pane.
- Try out all of these to learn how JSON path works! 

> I want: All Customers 

`$.*`

> I want: First Customer

`$.[0]`

> I want: Last Customer

`$.[-1:]`

> I want: First two customers

`$.[0:2]`

> I want: Last two customers

`$.[-2:]`

> I want: Second from last 

`$.[-2:-1]`

> I want: The the first customer

`$.[0]`

> I want: All the names

`$..name`

> I want: All the pins

`$..pin`

> I want: All the customers who’s pin value is more than 70000 or 80000

`$..[?(@.pin > 70000)]`

> I want: All details of customer with account number 

`$..[?(@.account == "87305901”)].*`

> I want: The the name of customer with account number 

`$.[?(@.account == "70579265")].name`
### 4. Configure the Conditional for Error Check
- Use the `httpBlock.StatusCode` variable to check the value retured.
- Note that the test API does not give a `404` but an empty list `[]` with a `200` when no match is found. However, this step is just to understand error handling and checking.
- Use the `{{ httpBlock.StatusCode == 200 }}` expression check on the condition and play success and failure prompts accordingly.
- Ensure all the settings are properly setup. 
- Validate and Publish the new script, correcting any errors that show up.

### 5. Point to the New flow in the Routing Strategy
- Go to the routing Strategy page > Routing Strategy > `EP_voice_wxcclab`
- Once the flow is published, configure the Entry Point Routing strategy to point to the new flow `advanced_flow2_wxcclab`.

### 6. Verify the flow end to end
- Verify the new flow end to end by first, logging into the Agent Desktop and going into a ready state.
- Ensure you're able to recieve the variables on the Agent Desktop.

Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Arunabh Bhattacharjee (arubhatt) | 10 Jan 2021 |

