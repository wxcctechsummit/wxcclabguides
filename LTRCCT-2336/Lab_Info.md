---
title: 'Lab Pre-requisites'
---

# Table of Contents

- [Lab Topology](#lab-topology)
- [Access URLs](#access-urls) 
- [Before starting the labs](#before-starting-the-labs)
- [Lab Support](#lab-support)

# Introduction
Digital channels are now more impactful than ever. 
These labs are specially designed for the Cisco Live session. The primary purpose of the labs is to give a clear understanding of New Digital Channels functionality. You will learn how to create and configure Webchat and SMS. Using the debug console, you will also get a clear understanding of troubleshooting issues.


## Lab Topology
<img align="middle" src="images/topology.png" width="1000" />

## Access URLs

| Component     | URL                     | Login                                                       |
| --------------- | ----------------------------------------- | -------------------------------------------------------------           |
| Webex CC Control Hub | [https://admin.webex.com](https://admin.webex.com){:target="_blank"} | cladmin**\<ID\>**@email.carehybrid.com |
| Management Portal | [https://portal.wxcc-anz1.cisco.com/portal](https://portal.wxcc-anz1.cisco.com/portal){:target="_blank"} | cladmin**\<ID\>**@email.carehybrid.com |
| Webex Connect | https://auclpod**\<ID\>**.au.webexconnect.io/ | cladmin**\<ID\>**@email.carehybrid.com |
| Agent Desktop | [https://desktop.wxcc-anz1.cisco.com](https://desktop.wxcc-anz1.cisco.com){:target="_blank"} | clagent**\<ID\>**@email.carehybrid.com |

> **NOTE:**  
> **\<ID\>** – is your unique POD ID listed on the card. \
> The lab POD is the same as the production tenant which is located in the ANZ Datacenter. These labs are for instructional purposes only but the configuration can be reused for the real deployment.
> The telephony service is not activated. This pod is used only for digital channels.

## Before starting the labs

1. Please confirm that you can login to WxCC Admin portal and Agent desktop by using the links above.

2. You have to use the admin account (with Administrator privileges) for access to Control Hub and Administration portal. 

3. Please follow the labs in the same order as they are provided.

### Users

The users have the following preconfiguration

| **User Role** | **User email**                       |
| ------------- | ------------------------------------ | 
| Agent         | clagent**\<ID\>**@email.carehybrid.com   | 
| Supervisor    | claup**\<ID\>**@email.carehybrid.com     | 

### User Settings

| **Entity**          | **Name** |
| ------------------- | -------- |
| Multimedia Profiles | MMP   |
| Site                | Site1  |
| Team1               | Team1 |
| Team2               | Team2 |

## Lab Support

1. Proctors are your number 1 contact. If you need assistance just raise your hand.

2. All registered participants are also added to the support room where engineering and Product Management team are added. As an alternative way, you can use that space for any questions related to the digital channels.

### May good fortune smile on you as you begin this new adventure :)
 

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2336/Home.html";}
function nextLab() 
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2336/Lab1_Preconfiguration.html";
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
