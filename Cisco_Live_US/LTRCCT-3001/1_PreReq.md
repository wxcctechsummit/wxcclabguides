---
title: 'Lab 1: Environment setup'
---

# Table of Contents

- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
    - [Lab Objective](#lab-objective)
    - [Pre-requisites](#pre-requisites)
    - [Quick Links](#quick-links)
- [Lab Section](#lab-section)
  - [Step 1. Node Authorization for Webex CC Task and Engage nodes](#step-1-node-authorization-for-webex-cc-task-and-engage-nodes)
  - [Step 2. Download and upload Channel Agnostic flows in Connect](#step-2-download-and-upload-channel-agnostic-flows-in-connect)
  - [Step 3. Setup agents in Portal (Agents, Team, MMP)](#step-3-setup-agents-in-portal-agents-team-mmp)
    - [Users](#users)
    - [User Settings](#user-settings)
    - [1. Create new MultiMedia Profile](#1-create-new-multimedia-profile)
    - [2. Create new Site](#2-create-new-site)
    - [3. Create new Teams](#3-create-new-teams)
    - [4. User Configuration](#4-user-configuration)
  - [Access to the Agent Desktop](#access-to-the-agent-desktop)


# Introduction

### Lab Objective

In this Lab, we will go through the tasks that are required to complete the general pre-configuration of a tenant. These tasks are to be undertaken by an administrator. By following each of the steps, you would have prepared your tenant to begin configuring different bot functionalities that are supported with the new digital channels. The lab contains multiple exercises to make you familiar with the Control Hub, Management portal UI and Webex Connect. At the end of the lab, you should be able to log in to an agent desktop interface and also complete the basic authentications required for working with Webex Connect application.


### Pre-requisites

1. You have received the access credentials with a full admin access 
2. You have received the access to the agent account


### Quick Links

> Control Hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="_blank"}**\
> Connect: https://cl2pod**X**.imiconnect.io/ (where **X** is your POD number)

# Lab Section

## Step 1. Node Authorization for Webex CC Task and Engage nodes

> Webex Connect is required to provide a valid access token for using various Webex Contact Center and imiengage APIs. The access token is generated using the authorization details configured within the ‘Node Runtime Authorization’ field that Webex Contact Center users are required to provide during flow configuration.

- Access the Webex Connect UI: https://cl2podX.imiconnect.io/ (where X is your POD number)

- To authorize a pre-built integration go to Assets > Integrations. The integrations which are not yet authorized show the status as **Pending Authorization**.

- In front of **Webex CC Engage** Click **Actions** → **Manage**.

<img align="middle" src="images/Import_Lab1_Integration1.gif" width="1000" />
<br/>
<br/>

- On the Manage Integrations page, scroll down to the Node Authorizations section. This section lists all the authorizations mapped to this integration.

- Click **Action** → **Add Authorization** associated with the authorization, where Auth Type is oauth2 and Status is Authorization Pending.

<img align="middle" src="images/Lab1_ManageIntegration1.png" width="1000" />

- Enter the Authorization Name and click **Authorize**. In that example we use **WebexCCAuth**\

<img align="middle" src="images/Lab1_WebexCCAuth.png" width="1000" />

- Click on the back button for being redirected back to **Integrations** page and in front of **Webex CC Task** Click **Actions** → **Manage**.

<img align="middle" src="images/Lab1_ManageIntegration2.png" width="1000" />

- On the Manage Integrations page, scroll down to the Node Authorizations section. This section lists all the authorizations mapped to this integration.

- Click **Action** → **Add Authorization** associated with the authorization, where Auth Type is oauth2 and Status is Authorization Pending.

<img align="middle" src="images/Lab1_ManageIntegration3.png" width="1000" />

- Enter the **Authorization Name** (for example: WxCCAuth) and click **Authorize**. As the result the pop-up appears where you need to enter your Cisco admin email address (cl1admin**X**@email.carehybrid.com) and click **Sign in**.

<img align="middle" src="images/Lab1_WebexCCAuth2.png" width="1000" />

> **!!!**: The status of the authorization will change to Authorized and all the nodes under this authorization are authorized and ready for use.
<img align="middle" src="images/Lab1_authorized2.png" width="1000" />


## Step 2. Download and upload Channel Agnostic flows in Connect 
> Every tenant must include Channel Agnostic (CA) flows. CA flows can be imported from the template folder in this [GitHub page](https://github.com/CiscoDevNet/webexcc-digital-channels){:target="_blank"}. CA flow can be added only once and will be automatically be used by all existing channel specific flows in the tenant when needed. Recommended to add these flow in a dedicated Service named “Agnostic Flows - DO NOT MODIFY”

> The agnostic flows consist of:\
> • Task Routed - Adding an agent participant to a conversation;\
> • Task Modified - Adding an agent to or removing an agent from an ongoing conversation (e.g., for chat transfer or conference);\
> • Task Close - Closing the conversation;

1) Download all flows from the [GitHub page](https://github.com/CiscoDevNet/webexcc-digital-channels){:target="_blank"}.

2) Navigate to **Webex Connect Flows** -> **v2.1**.

3) Unzip All Files.

4) Login to the **Webex Connect** portal with the admin account.

5) Navigate to **Services** and click on **CREATE NEW SERVICE**

<img align="middle" src="images/Lab1_Services.png" width="1000" />

6) Set your name __Agnostic Flows DO NOT MODIFY__ in the Service Name. This will create a new service.
> **Note** You can choose a different Service name. It is just an exmple.

7) In the service click on **FLOWS** -> **CREATE FLOW**

<img align="middle" src="images/Lab1_Flows.png" width="1000" />

8) In the **FLOW NAME** section set **Task Close Flow**

9) In the **METHOD** select **Upload a flow**. In **ATTACHMENT** click on **CHOOSE FILE** and select the **Task Close Flow.workflow** file

10) Now you can click on **CREATE** button

<img align="middle" src="images/Lab1_Create.png" width="1000" />

11) In the new menu click on **SAVE** and then **MAKE LIVE**. You should get the message that "Flow successfully made live"

<img align="middle" src="images/Lab1_Live.png" width="1000" />

12) Repeate steps 7 - 11 for **Task Routed flow** and **Task Modified Flow**


## Step 3. Setup agents in Portal (Agents, Team, MMP)

> This step shows how to access the admin portal and navigate the different configuration menus to create a Site, Team, and Multimedia Profile that will be assigned to the Contact Center user. 


### Users

The users have the following preconfiguration

| **User Role** | **User email**                       |
| ------------- | ------------------------------------ | 
| Agent         | cl2agent**\<ID\>**@email.carehybrid.com   | 
| Supervisor    | cl2sup**\<ID\>**@email.carehybrid.com     | 

> **Note:** Your \<ID\> was provided to you personally.  \<ID\> is the unique number equal to your POD.

### User Settings

| **Entity**          | **Name** |
| ------------------- | -------- |
| Multimedia Profiles | MMP   |
| Site                | Site  |
| Team1               | Team1 |
| Team2               | Team2 |


### 1. Create new MultiMedia Profile

- Login to Managment Portal by accessing [https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="\_blank"}.

- Enter the admin email address (cl2admin\<ID\>@email.carehybrid.com) and click **Sign in**

- Click on **_Provisioning_** and select **_Multimedia Profiles_**.

- Click on `+ New Multimedia Profile` to open Multimedia Profile configuration page.

- Input Name as `MMP`.

- In the Media Details section, select the blended multimedia profile and input `1` for **_Voice_**, `3` for **_Chat_**, `3` for **_Email_**, , `3` for **_Social Channel_** and click on **_Save_** button.

<img align="middle" src="images/Lab1_MMP.png" width="1000" />


### 2. Create new Site

- Navigate to **_Provisioning_** and select **_Site_**.

- Click on `+ New Site` button and provide the Name as `Site`.

- Select `MMP` in the **_Multimedia Profile_** drop down and hit **_Save_**.


<img align="middle" src="images/Lab1_Site.png" width="1000" />


### 3. Create new Teams

- Navigate to **_Provisioning_** and select **_Team_**.

- Click on `+ New Team`.

- Select `Site` from the **_Site_** drop-down.

- Input **_Name_** as `Team1`.

- Use the default **_Type_** `Agent Based`.

- Select `MMP` in the **_Multimedia Profile_** drop-down.

- Left as a default value **_Global Layout_** in the **_Desktop Layout_** drop-down and hit **_Save_**.

<img align="middle" src="images/Lab1_Team.png" width="1000" />

- Please follow the same steps as above to add an extra Team as `Team2`. 

[To top of this lab](#table-of-contents)

### 4. User Configuration

- Click on **_Provisioning_** and select **_Users_**.

- Click on `...` for the **Agent** user, to launch the **_Edit_** view for a particular User configuration.

- Make sure that the **_User Profile_** is set as **_Premium Agent User Profile_** 

- Click on **_Contact Center Enabled_** toggle to move it to **_On_**.

- In the **_Agent Settings_** section, select `Site` in the **_Site_** drop-down.

- Click the **_Teams_** area and select `Team1` and `Team2`.

- Select `Agent Profile` in the **_Agent Profile_** drop-down list.

- Select `MMP` in the **_Multimedia Profile_** drop-down and hit **_Save_**.

- Make sure that the user are now shown with the **_Contact Center Enabled_** flag as `Yes` and **_Status_** as `Active`.

<img align="middle" src="images/Lab1_User.png" width="1000" />

- Please follow the same steps for **Supervisor** user. 





## Access to the Agent Desktop
> **Note**: To log in to the agent desktop, use either a separate web browser or a new incognito web page. This will prevent any browser caching issues with admin and agent credentials.

- Navigate to **[https://desktop.wxcc-us1.cisco.com/](https://desktop.wxcc-us1.cisco.com/){:target="_blank"}** in a new browser or in incognito mode.

- Enter the agent’s **email ID** `cl2agentX@email.carehybrid.com`.

- Enter the **Password** for the appropriate Username.

- In the **_Station Login_** pane, select **"Extension"** and put any number, for example, 1000

> **Note:** The Webex Calling service is not activated at this tenant we need to set an extension only once during login.

- Select the `Team1` and click **_Submit_**. Make sure that you are successfully logged in to the Agent Desktop. Now you can continue with the next section.

<img align="middle" src="images/Lab1_Login.png" width="1000" />


[Back to top](#table-of-contents)



---

### Congratulations, you have completed Lab1 tasks! 

<script>
function mainPage() {window.location.href = "https://ciscolivelabs.github.io/wxcclabguides/LTRCCT-3001/0_LabInfo.html";}
function nextLab() 
 {
 window.location.href = "https://ciscolivelabs.github.io/wxcclabguides/LTRCCT-3001/2.1_BasicChat.html";
 }
</script>

<div id="button-row">
<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go To Previous Lab</button>

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go to the Next Lab</button>

</div>

