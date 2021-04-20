---
title: "Lab 1: Control Hub And Admin Portal"
---

### Overview of the lab:

In this Lab, we will go through the tasks that are required to complete the general pre-configuration of a tenant. These tasks are to be undertaken by a customer administrator. By following each of the steps, you would have prepared your tenant to begin configuring different services offered by the platform. At the end of the lab, you should be able to log in to an agent interface with the configured user extension.

# Table of Contents

- [Part 3: Control Hub User Management Admin Task](#part-1-control-hub-user-management-admin-task) 
  * [1. Add an agent and a supervisor users and configure the calling extension](#1-add-an-agent-and-a-supervisor-users-and-configure-the-calling-extension)
  * [2. Optionally, add the rest of the users](#2-optionally-add-the-rest-of-the-users)
- [Part 4: Admin Portal Multimedia Profile, Site and Team Configuration](#part-2-admin-portal-multimedia-profile-site-and-team-configuration)
  * [1. Create new MultiMedia Profile](#1-create-new-multimedia-profile)
  * [2. Create new Site](#2-create-new-site)
  * [3. Create new Team 1](#3-create-new-team-1)
  * [4. Create new Team 2](#4-create-new-team-2)
- [Part 5: Admin Portal User Configuration](#part-3-admin-portal-user-configuration)
  * [1. Synchronize Webex Contact Center Users](#1-synchronize-webex-contact-center-users)
  * [2. Manage settings for existing user](#2-manage-settings-for-existing-user)

# Introduction

### Lab Objective

- This lab is designed to help you to be familiar with the control hub and admin portal UI. 
- The lab contains multiple exercises on Control Hub and Admin Portal to make you comfortable with the Webex Contact Center application.

### Pre-requisites

- You have an assigned **POD ID** and your **attendee ID**.
- You have recived the **admin login** credentials.
- You have the **calling DNIS**.
- You have the agent/supervisor **extension** numbers.

### Quick Links
> Control Hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\
> Mailinator: **[https://www.mailinator.com/](https://www.mailinator.com/){:target="_blank"}**


# Lab Section

## Part 3: Control Hub User Management Admin Task

> The following video outlines the process to manage different types of users to the Customer tenant. Following the steps, you will add new users and set the extension. While adding the user, we will see how to select user roles. 

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/b_o-0XoJVMw?rel=0" title="WxCC Lab #1 Part 1: Control Hub User Management Admin Task" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


| **User Role** | **User email**      | **User Extension**                   |
| ----------- | ----------------- | -------------------------------- |
| Agent        | agent1_\<ID\>@mailinator.com   | 1000 |
| Supervisor         | supervisor1_\<ID\>@mailinator.com  | 2000 |

> **NOTE:** Your \<ID\> is provided in the email in the **"Attendee ID"** line.

### 1. Add an agent and a supervisor users and configure the calling extension

- Login to the [Control Hub](https://admin.webex.com){:target="_blank"} with the admin account.

- Navigate to **_Users_**.

- Click on **_Manage Users_** button.

- Click on **_Manually Add or Modify User_**.

- Select **_Next_** in **_Manage Users_** pane.

- Input the **Email addresses** of the agent and supervisor users and click **_Next_**. 

- Verify that the **Email addresses** are same as in the table above and click **_Next_**.

- Check **_Webex Teams_** , **_Webex Calling (Enterprise)_** & **_Contact Center_**.

- Ensure that the License Type is **_Premium Agent_** and Role is **_Agent_** and click **_Next_**. 

- On the next page, make sure that the **_Location_** is selected under **_Assign Numbers_**. The correct value should be already selected by default. 

- The **_Phone Number_** left as **None**.

- On the same page, Enter the correct `Extension` under **_Assign Numbers_**. You can find this in the table above.

- Click **_Finish_**.

- On the next page, you should get confirmation **"2 Total records processed"**. Confirm the same by pressing **_Finish_**.

- Select the supervisor user and modify his role to **_Supervisor_** by clicking the top **_Edit_** button in front of **_Services_**. Click **_Save_** to confirm the changes.

- Validate the users by going to [https://www.mailinator.com/](https://www.mailinator.com/){:target="_blank"} and putting agent/supervisor email in to **_Enter Public Mailinator Inbox_** 

> **Note:** You do not need a password to open the inbox on mailinator. You can read any emails without mailbox credentials. Just insert agent name in the top right form and click **GO**.
> ![Mailinator](../images/mailinator.png)

- Check the email inboxes and follow the **Cisco Webex** email instructions to activate the user accounts. For the user activation, you have to set the password twice for both users.

- Refresh the **_Users_** page in the Control Hub, make sure that all users are in **Active** status.

### 2. Optionally, add the rest of the users

- Follow the same steps as above to add any extra users that you want to add to the Contact Center.

[To top of this lab](#table-of-contents)

## Part 4: Admin Portal Multimedia Profile, Site and Team Configuration

> The following video outlines how to access the admin portal and navigate the different configuration menus to create a Site, Team, and Multimedia Profile that will be assigned to each different Contact Center Users. We will also see how to navigate to the Webex Contact Center Management Portal from Control Hub UI.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/G9yWf_dk2D0?rel=0" title="WxCC Lab #1 Part 2: Admin Portal Multimedia Profile, Site and Team Configuration" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


| **Entity** | **Name**      | 
| ----------- | ----------------- | 
| Multimedia Profiles        | MM_Profile_wxcclab_\<ID\>   | 
| Site         | Site_wxcclab_\<ID\>  | 
| Team1         | Team1\_wxcclab_\<ID\> | 
| Team2         | Team2\_wxcclab_\<ID\>  | 

> **NOTE:** Your \<ID\> is provided in the email in the **"Attendee ID"** line.

### 1. Create new MultiMedia Profile

- Login to Control Hub by accessing [https://admin.webex.com](https://admin.webex.com){:target="_blank"}.

- Enter the admin email id and the password.

- Navigate to **_Contact Center_** Card.

- Click **_Settings_** in the upper right corner.

- Scroll down to the **_Advanced Configuration_** section.

- Click on **_Go to Webex Contact Center Management Portal_**.

- Ensure that browser pop up blockers are not blocking the **_Admin Portal_** pop up.

- Click on **_Provisioning_** and select **_Multimedia Profiles_**.

- Click on `+ New Multimedia Profile` to open Multimedia Profile configuration page.

- Input Name as `MM_Profile_wxcclab_<ID>` and input `1` for **_Voice_**, `3` for **_Chat_**, `3` for **_Email_**, `3` for **_Social Channel_** and click **_Save_**.

### 2. Create new Site

- Navigate to **_Provisioning_** and select **_Site_**.

- Click on `+ New Site` button and provide the Name as `Site_wxcclab_<ID>`.

- Select `MM_Profile_wxcclab_<ID>` in the **_Multimedia Profile_** drop down and hit **_Save_**.

### 3. Create new Team 1 

- Navigate to **_Provisioning_** and select **_Team_**.

- Click on `+ New Team`.

- Select `Site_wxcclab_<ID>` from the **_Site_** drop-down.

- Input **_Name_** as `Team1_wxcclab_<ID>`.

- Use the default **_Type_** `Agent Based`.

- Select `MM_Profile_wxcclab_<ID>` in the **_Multimedia Profile_** drop-down.

- Left as a default value **_Global Layout_** in the **_Desktop Layout_** drop-down and hit **_Save_**.

### 4. Create new Team 2

- Please follow the same steps as above to add an extra Team as `Team2_wxcclab_<ID>`. Later we will use this team to assign a custom Desktop Layout.

[To top of this lab](#table-of-contents)

## Part 5: Admin Portal User Configuration

>The following video outlines how to configure the users in Admin Portal that were added first in Control Hub. This is a very critical task from the Contact Center perspective. We also would take a look at how to associate customer-created Site, Team, and Multi-Media Profile with those users. After this, we should be able to login as an agent using any of the users and their associated extension.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/Y5bmhAw_gBg?rel=0" title="WxCC Lab #1 Part 3: Admin Portal User Configuration" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 1. Synchronize Webex Contact Center Users

- Login to Control Hub by accessing [https://admin.webex.com](https://admin.webex.com){:target="_blank"}.

- Enter the admin email id and the password.

- Navigate to **_Contact Center_** card/

- Click on **_Settings_** and then `Synchronize Users`.

### 2. Manage settings for existing user

- Go back to the **_Webex Contact Center Management Portal__**.

- Click on **_Provisioning_** and select **_Users_**.

- Click on `...` for the first user, to launch the **_Edit_** view for a particular User configuration.

- Click on **_Contact Center Enabled_** toggle to move it to **_On_**.

- In the **_Agent Settings_** section, select `Site_wxcclab_<ID>` in the **_Site_** drop-down.

- Click the **_Teams_** area and select `Team1_wxcclab_<ID>` and `Team2_wxcclab_<ID>`.

- Select `MM_Profile_wxcclab_<ID>` in the **_Multimedia Profile_** drop-down and hit **_Save_**.

- Repeat the same for all other users by selecting the appropriate profile in the **_User Profile_** drop down.

- Make sure that both users are now shown with the **_Contact Center Enabled_** flag as `Yes` and **_Status_** as `Active`.

[To top of this lab](#table-of-contents)

### Congratulations, you are now ready to start the next section!


<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LabLibrary";}
function nextLab() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/labs/lab1.html";}
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
  padding: 10px;">Next Lab 2: Exploring the Agent Desktop</button>
  
</div>

