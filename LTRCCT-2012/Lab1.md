---
Title: 'Lab 1: Contact Queueing to Agent Desktop '
---

# Table of Contents

- [Table of Contents](#table-of-contents)
- [Introduction](#Introduction)
    - [Recap](#Recap)
    - [Lab Objective](#lab-Objective)
    - [Pre-requisites](#pre-requisites)
    - [Quick Links](#quick-links)

- [Lab Section](#lab-section)
  - [Step 1. Site Team Agent](#Site-Team-Agent)
  - [Step 2. AgentLogin](#AgentLogin)
  - [Step 3. Flow configuration](#Flow-configuration)

-[Lab Validation](Lab-Validation)



# Introduction

### Recap

 In the first Lab, we Learned
 0. Bring the contact into Webex Contact Center and hear  welcome message


### Lab Objective

In this section, we will go over the steps that are required to Login an Agent and Queue contact to an Agent . In this Lab you will learn the following
1. Creating Site, Queue, Team
2. Agent Desktop Login
3. Enhance the Flow created in Lab 0 to add steps to queue contact to Agent




### Pre-requisites

- Basic IVR flow worked, caller can connect to WXCC and hear welcome music



### Quick Links

> Control Hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="_blank"}**\

<img align="middle" src="Images/Lab1/Flowchart1.jpg" width="1000" />


# Lab Section

## Step 1. Site Team Agent

> **Site** -- A site is a physical contact center location under the control of your enterprise. For example, enterprise Acme can have sites in Chicago, Manila, and Bangalore with agents to handle customer contacts.

To create a Site, Login to portal-->Provisioning-->Sites

<img align="middle" src="Images/Lab1/Site.jpg" width="800" />

>.

<img align="middle" src="Images/Lab1/Site1.jpg" width="800" />

>


- **IMPORTANT NODE** For this lab, we use the site tagged to admin user,  check your admin user and create team part of the same site

### Team
>**TEAM** -- A team is a group of people who support a specific group of functions. For example, supporting the Gold customers or managing billing, and so on. A team consists of agents.

To create a Site, Login to portal-->Provisioning-->Teams

<img align="middle" src="Images/Lab1/Team.jpg" width="500" />

> Team is tagged to the site, and agents will login into team.
Agent can have Skill and multimedia profile at the team level.If agents has skill and multimedia profile configured under **Users** that supersedes the one configured at team level

<img align="middle" src="Images/Lab1/Team1.jpg" width="900" />

### Agent aka Users

>All the users added at control hub are by default synched to WxCC portal under **Provisioning-->Users**  Based on the user profile, a User take different role(Agent, Supervisor, Administrator)



<img align="middle" src="Images/Lab1/Users.jpg" width="900" />


> User with premium Agent license can log in as Agent as well as perform Admin tasks

> **Note** In this Lab, we will using Admin user as Agent as well.

<img align="middle" src="Images/Lab1/Profiles.jpg" width="800" />

- **IMPORTANT NODE** For this lab, use Default Agent and Multimedia profile


### Create Queue

1. From portal -->provisioning -->Create new queue
2. add call distribution group aka Teams
3. make sure give service level threshold time (preferably 3600) and service level threshold

<img align="middle" src="Images/Lab1/queue1.jpg" width="300" />
<img align="middle" src="Images/Lab1/queue2.jpg" width="600" />
<img align="middle" src="Images/Lab1/queue3.jpg" width="600" />


## Step 2. AgentLogin

1. Download Webex Client from this [link](https://settings.webex.com/login)
2. Login with Admin Credentials
3. click on Webex Calling -->My Apps and Download Webex apps -- https://www.webex.com/downloads.html
4. Login to Webex apps using same admin credentials

<img align="middle" src="Images/Lab1/webexcallingpage.jpg" width="200" />
<img align="middle" src="Images/Lab1/webexappdownload.jpg" width="200" />
<img align="middle" src="Images/Lab1/webexsignin.jpg" width="200" />

> If the webex app is already in the system, you can skip first 2 steps

> Using below link to login to agent desktop  alternatively you can cross launch from portal also

Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com)

<img align="middle" src="Images/Lab1/Desktop_Crosslaunch.jpg" width="400" />

> While login into agent desktop make sure to choose **Extension** and correct **Team**

<img align="middle" src="Images/Lab1/stationlogin.jpg" width="200" />
<img align="middle" src="Images/Lab1/agentstatus.jpg" width="200" />
<img align="middle" src="Images/Lab1/team&profile.jpg" width="200" />




## Step 3. Flow configuration

1. Copy the Lab0 flow by clicking on 3 dot <img align="middle" src="Images/Lab1/copyflow.jpg" width="200" />
2. open the copy of Lab 0 and rename it to Lab1 <img align="middle" src="Images/Lab1/flowrename.jpg" width="400" />
3. Delete Disconnect node and add Queue node and play music node, loop back play music as shown below


 <img align="middle" src="Images/Lab1/flow2.jpg" width="400" />

4. select queue created above and the **0_MOH** for music

<img align="middle" src="Images/Lab1/selectqueue.jpg" width="500" />
<img align="middle" src="Images/Lab1/selectmusic.jpg" width="500" />

5. Validate the flow and publish the flow

6. change **current** routing strategy and change the flow from Lab0 to Lab1

<img align="middle" src="Images/Lab1/Rschange.jpg" width="500" />

# Lab Validation

- i) Dial the Number

-  ii) Login into Agent Desktop and Keep the Agent in Not Ready State

- Expected Result

  i) Caller should hear welcome voice prompt

  ii) Call Should get queued to agent

  iii) Make Agent Available, call should be routed to  agent desktop and there is 2 way voice between agent and customer



### Congratulations, you have completed Lab1 tasks!











---



<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2012/Home.html";}
function nextLab()
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2012/2_Lab2.html";
 }
</script>

<div id="button-row">
<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Home Page</button>

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go to the Next Lab</button>

</div>
