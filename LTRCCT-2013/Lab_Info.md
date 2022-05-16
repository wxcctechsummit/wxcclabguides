---
title: 'Lab Pre-requisites'
---
## Introduction
Digital channels are now more impactful than ever. 
This labs are specially designed for the Cisco Live session. The main purpose of the labs is to give a clear understanding of New Digital Channels functionality. You will learn how to create and configure all digital channels including Chat, Email, Facebook, and SMS. You will get a clear understanding of the scripts' logic and how to troubleshoot issues by using the debug console.

## Lab Topology
<img align="middle" src="images/topology.png" width="1000" />

## Access URLs

| Component     | URL                     | Login                                                       |
| --------------- | ----------------------------------------- | -------------------------------------------------------------           |
| Webex CC Control Hub | [https://admin.webex.com](https://admin.webex.com){:target="_blank"} | cl1admin**X**@email.carehybrid.com |
| Management Portal | [https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"} | cl1admin**X**@email.carehybrid.com |
| IMI Connect | https://cl1pod**X**.imiconnect.io/ | cl1admin**X**@email.carehybrid.com |
| Agent Desktop | [https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="_blank"} | cl1agent**X**@email.carehybrid.com |

> **NOTE:**  
> **X** – is your unique POD ID listed on the card. \
> The lab POD is the same as the production tenant which is located in the US Datacenter. These labs are for instructional purposes only but the configuration can be reused for the real deployment.
> The telephony service is not activated. This pod is used only for digital channels.

## Before starting the labs

1. Please confirm that you can login to WxCC Admin portal and Agent desktop by using the links above.

2. You have to use the admin account (with Administrator privileges) for the access to the Control Hub and Administration portal. 

3. Agent desktop login should use a user with  premium agent license ONLY. If agent is also assigned admin roles, this could cause issue with accepting digital contacts.

4. Please follow the labs in the same order as they are provided. Some of the lambs would have dependencies.

### Users

The users have the following preconfiguration

| **User Role** | **User email**                       |
| ------------- | ------------------------------------ | 
| Agent         | cl1agent**X**@email.carehybrid.com   | 
| Supervisor    | cl1sup**X**@email.carehybrid.com     | 

### User Settings

| **Entity**          | **Name** |
| ------------------- | -------- |
| Multimedia Profiles | MMP   |
| Site                | Site  |
| Team1               | Team1 |
| Team2               | Team2 |

## Lab Support

1. Proctors is your number 1 contact. If you need assistance just raise your hand.

2. All registered participants are also added to the support room where the engineering and Product Management team is added. As an alternative way, you can use that space for any questions related to the digital channels.

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2013/Home.html";}
function nextLab() 
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2013/Ex1.html";
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
