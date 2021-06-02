---
title: 'Lab 2: IVR and Contact Routing'
---

# Table of Contents

- [Part 1: Setup a Simple Flow and make a test call](#part-1-setup-a-simple-flow-and-make-a-test-call)
  - [1. Verify that your users are ready to login](#1-verify-that-your-users-are-ready-to-login)
  - [2. Create the Voice Entry Point and Voice Queue](#2-create-an-inbound-voice-entry-point-and-voice-queue)
  - [3. Verify/Upload the Audio Prompts, Create the Entry Point Flow.](#4-verify-the-audio-prompts-create-the-entry-point-flow)
  - [5. Configure and Publish the Flow](#5-configure-and-publish-the-flow)
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

- The lab will also contain multiple exercises on flow designer to make you comfortable with the Webex Contact Center Flow Designer and the overall Contact Routing configuration.

- **IVR Prompts:** We will expect you to configure and upload static prompts shared for use below. You may also choose to use dynamic TTS prompts, it will not change the lab or its content. You can upload these "CiscoDemo" prompts and use them for the labs. You may also keep a copy of the zip file if you want to manually upload them. In the bonus lab sections, we also share how you can convert these prompts to dynamic TTS prompts using the Text to speech connector configuration available within flow designer.

> ### [Download the IVR Prompts - Static Prompts HERE](https://cisco.box.com/s/fvr4k0nay93lyjnxaqxwevbcts5glbsu){:target="\_blank"}

- **Lookups, Advanced Scripting, Screen-pops:** We have chosen specific areas of focus for advanced scripting topics. We have more content shared in the bonus sections on how to get other use cases configured.

- **GoTo, ScreenPops, Skills Based Routing:** We will cover the newer features on Webex Contact Center, including the GoTo step, Screen Pop, and skills based routing.

# Lab Pre-requisites

1. **Webex Calling App** is installed on your **PC or MAC, and Mobile.**
 	- PC or MAC Webex calling App for Agent to accept calls.
 	- Mobile Webex Calling App for Supervisor to accept calls and to place test calls to EP.
2. All the tasks from **Lab1 (Control Hub and Admin Portal)** are completed.
	- You have the administrator's access to the Tenant Management Portal.
	- Agent and Supervisor users created and configured
	- You have agent's access to the Agent Desktop
	- You have the supervisor's access to the Tenant Management Portal.
	- Agent is part of 2 Teams.
	- Webex Calling extensions are assigned to a WxCC users (agent and supervisor).
3. This lab assumes that you are comfortable with your current Webex Contact Center in your Gold Tenant.


**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="\_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="\_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

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

- Go to `Provisioning -> Users` to check the `Site` that the user is assigned to. Ensure that the `Team` is created under the right `Site`.

- If you would like to Create a Team, create the `Team` under that `Site` - and assign the `Team` to the Agent.

> **WARNING** `Agent` > `Site` relationship cannot be changed. So all teams will need to be created under the same site.

- With the steps outlined in the previous lab, you should now be able to login to the **[Agent Desktop](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

> **NOTE:** Only teams that are in the same site of the Agent will be visible to assign to the agent.


### 2. Create an inbound Voice Entry Point and Voice Queue

- Login to Portal and create an inbound voice entry point and voice queue. (Provisioning > Entry Point / Queue).

- Create the Entry Point named `EP_<ID>_TS`.

- Create the Queue named `Q_<ID>_TS`.

**Here are the Queue Settings**

| Configuration                       | field Value             |
| ----------------------------------- | ----------------------- |
| Name                                | `Q_<ID>_TS`             |
| Channel Type                        | Telephony               |
| _---- Contact Routing Settings ---_ |
| Queue Routing Type                  | Longest Available Agent |
| Call Distribution                   | `<Add team>`            |
| _---- Advanced Settings ---_        |
| Service Level Threshold             | 60                      |
| Maximum Time in Queue               | 600                     |
| Time Zone                           | Default                 |

---

- Please see below note if your POD is shared with other members. 

> **NOTE:**  If you are sharing the tenant with other members on your team, each one can create their own call flow but use the IVR under the DN EP to help make the decision on what flow you want the call to take. e.g. Map DN to `EP_Main_TS' > Flow_Main, then branch out to your  `EP_<ID>_TS` from Flow_Main.

- Mapping the DN to the Entry Point:
In the Portal, under Entry Point Mappings page (Proivisioning > Entry Point Mappings), map the listed DN to `EP_<ID>_TS`. 

### 3. Verify the Audio Prompts, Create the Entry Point flow.

- The audio prompts required for the script build out are wav files. The whole bundle of wav files are given below

[Download the IVR Prompts - Static Prompts HERE](https://cisco.box.com/s/fvr4k0nay93lyjnxaqxwevbcts5glbsu){:target="\_blank"}

> **Note:** Upload the audio files under > Routing Strategy (from Portal) > Resources > Audio Files.

### 4. Configure and Publish the flow

- Configure the flow `Flow1<ID>` with a Play prompt - welcome message and Disconnect
- Configure the flow `Flow1<ID>` with a Play prompt - welcome message and queue block and play music block.
- Configure the Queue Block to `Q_<ID>_TS`. Map the queue inside of the queue block.
- Configure the play music to loop, and start 0, end 10 to play 10 seconds of music.
- Verify and publish the flow.

### 5. Configure the Entry Point Routing Strategy

- Configure the Open 24x7 routing strategy time of day on the Entry Point Routing strategy by selecting it on the Routing Strategies >`EP_<ID>_TS`.
- Map the flow flow1_<ID> you just created in there.

### 6. Make a test call

- Login to the agent desktop into `Team_<ID>_TS` and go to a ready state.

- Task 1 > Call the Dial number > Hear the welcome prompt and call should get disconnected.
- Task 2 > Call the Dial number > Available agent gets connected immediately, If the Agent is not available the call is queued and music is played.

---

## Congratulations! You're done with Part 1!

## You are ready to start Part 2!

# Part 2: Adding Menu and Queue treatment to the call

> This lab is designed to help you configure a Menu step in the call flow along with Queue Treatment. We will also configure counters and Opt-outs within the queue, along with Callbacks.

> At the end of this lab, you should be able to hear a Menu prompt, Opt-out of queue, and send a courtesy callback call to the customer by picking a ready agent.

<iframe width="1024" height="576" src="https://www.youtube.com/embed/BKid4Q--dp0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="\_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="\_blank"}**\
> Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

## Steps

### 1. Copy out the flow and configure the advanced flow

- Open the Portal > Routing Strategy > Flow page.
- Copy the existing flow `Flow1_<ID>` and edit the copied flow - name it `Flow2_<ID>`
- Edit the flow to go into flow designer.
- Ensure that you configure the Menu steps with a 3 options - for example 1 & 2 to go to a queue and 3 Blind Transfer to external number.
- Ensure you configure all the fields in the menu step including the prompts and the entry timeout (requires you to explore all options on the step).
- Ensure you configure all the blind transfer location to Cisco Toll Free : `+18005536387`

  > **Note: This will actually connect you to the live toll free number!**

> **Important TIP on the MENU Block**

> `Make all Menu Steps Interruptible by default` - This gives callers an option to bypass the prompt. It is a small checkbox on the Menu Step.

> `In the Menu Block > Advanced Settings > Entry Timeout = Make it 10 Seconds` - This gives callers enough time to complete the DTMF (digit) entry.

---

### 2. Configure the Queue Treatment loop and Opt Out and Callback steps

- In Flow Designer - Configure the Queue treatment for the first queue. Use the queueCounter variable and configure the Opt out steps including the high volume message and the callback step.
- Configure the voicemail destination to the same Cisco Toll Free number above.
- Validate the flow and publish it.

### 3. Plug In New Flow into Routing Strategy

- Go to the routing Strategy page > Routing Strategy > `EP_<ID>_TS`
- Once the flow is published, configure the Entry Point Routing strategy to point to the new flow `Flow2_<ID>`

### 4. Test the end to end flow

- Login to the agent desktop and go Idle (Not Ready)
- Test Queue treatment by going not ready on the agent desktop.
- Call the main number on the entry point and go into the queue. You should hear the queue twice and then have an option to leave a callback.
- leave the callback and the call should end.

### 5. Execute the Callback

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
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

## Steps

### 1. Verify/create the Outdial Entry Point and Queue

- Login to Portal > Provisioning > Outdial Entry Point > Configure an Outdial Entry Point.
- Verify you already have an outdial Queue configured on Portal > Provisioning > Outdial Queue.
- Ensure that the system created outdial entry points and queues are present and configure their settings.
- Alternatively, you can setup a new Outdial Entry Point as shown in the video.

### 2. Create the Outdial Entry Point Routing Strategy

- Go Routing Strategy > Choose the One you just setup OR the default Outdial Entry Point-1
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
- Test it by calling the Cisco Tollfree Number - `+18005536387` –Note: This will actually connect you to a live toll free number for Cisco Support!
- You should have all the connected call features pop on the agent desktop once the call is established and the call should land on your Calling endpoint.

---

## Congratulations! You're All done with the Part 3! Now onto Part 4!

---

# Part 4: Advanced Scripting Steps - HTTP Request

<iframe width="1024" height="576" src="https://www.youtube.com/embed/gXhVTkGazmk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="\_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="\_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

## Steps

### 1. Copy out the flow and configure the advanced flow 2

- Open the Portal > Routing Strategy > Flow page.
- Copy the existing flow `Flow2_<ID>` and edit the copied flow - name it `Flow3_<ID>`
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

- Create 4 Custom variables - mark them CAD variables - with names `name`,`email`,`phone`, `account` with labels `Name`, `Email`, `Phone`, `Account` and values of `None` OR `null` - _(depends on what you prefer as the default for the agents to see if no info is available in the data dip)_

> The actual request we will construct is :

**HTTPS GET -> https://5f97898842706e0016957443.mockapi.io/crm/api/customers?pin=18716**

- Use the variable from the CollectDigits1.EnteredPIN variable to inject it in the pin lookup.
- We will construct it as follows

```
HTTP Request
GET https://5f97898842706e0016957443.mockapi.io/crm/api/customers

Query    <->     Parameters
pin      <->     {{CollectDigits.DigitsEntered}}

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

- Go to the routing Strategy page > Routing Strategy > `EP_<ID>_TS`
- Once the flow is published, configure the Entry Point Routing strategy to point to the new flow `Flow3_<ID>`.

### 7. Verify the flow end to end

- Verify the new flow end to end by first, logging into the Agent Desktop and going into a ready state.

Execute the Test:

- Call the Dial number > Enter the 5 digit PIN number as `18716` > On Main Menu press 2 > call gets connected to agent,

`Agent should see all CAD variables (Customer Name, Email, Account Number)`

---

## Congratulations! You're done with Part 4!

## You are ready to start Part 5!

---

# Part 5: Skills Based Routing - Contact Priority - Skill Relaxation

<iframe width="1024" height="576" src="https://www.youtube.com/embed/b-KyHUia-Bk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="\_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="\_blank"}**\
> Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="\_blank"}**\

## Steps

### 1.Create new Queue with Skill based routing and Add team

- Open portal > Provisioning > Entry point/Queue > Queue
- Create new Skills Based Queue > Give Name and Description
- Channel Type > `Telephony`
- Queue Routing Type > Skill Based > Best Available Agent
  Add Team > `Team_<ID>_TS`

| Configuration field        | Value                |
| -------------------------- | -------------------- |
| Name                       | `Q_<ID>_TS_SBR`      |
| Channel Type               | Telephony            |
| _Contact Routing Settings_ |
| Queue Routing Type         | Skills Based         |
| Agent Selection            | Best Available Agent |
| Call Distribution          | `<Add team>`         |
| Service Level Threshold    | 60                   |
| Maximum Time in Queue      | 600                  |
| Time Zone                  | Default              |

### 2.Create Skill Definitions

- Open portal > Provisioning > Skill > Skill Definition
- Click (New Skill Creation) > Give Name(`SkillSet`)and Description(`Skillset`) Type > `Proficiency`
- Click (New Skill Creation) > Give Name(`VIP Customer`)and Description(`VIP Customer`) Type > `Text`

> **Note:** We are using "TEXT Skills" in this SBR lab so that you can directly target agents with a specific variable from flow. This gives powerful capabilities as you will see later.

### 3.Crete Skill Profile

- Open portal > Provisioning > Skill > skill Profile
- Click (New Skill Profile) > Give Name - `TechSummitSkill` and Description -`TechSummitSkill`
- Select `SkillSet` and enter the Skill Value as `8`
- Select `VIP Customer` and enter the `Skill Value` to `Techsummit`

### 4. Add skill profile to User/ Agent

- Open Portal > Users
- Edit User > Under Skill Profile select the skill profile created in step 2 - `TechSummitSkill`

### 5. Modify the Previous Flow into a new Flow 4

- Open Flow > Copy Existing Flow 2 - Rename it as Flow 4.
- In Option 1 > Select the Queue Block > Make it SBR based by selecting the Skills Based Queue.
- Setup skill requirements as below

**Set the following settings**

> `Skillset >= 5`

> `Make {{skill}} as a String Variable`

> `VIPCustomer` IS {% raw %}{{skill}}{% endraw %}

> Enable Skill Relaxation After waiting in queue for: `15 seconds`

**Set skill relaxation to (after 60 seconds):**

> `Skillset >= 3`

> Remove the requirement of the VIP Customer skill.

---

## Congratulations! You're done! Test your skill based routing now.


----

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/TechSummitRoW_2021/HomePage.html";}
function nextLab() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/TechSummitRoW_2021/Lab3.html";}
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
  padding: 10px;">Next Lab 3: Agent and Supervisor Desktop</button>


</div>
