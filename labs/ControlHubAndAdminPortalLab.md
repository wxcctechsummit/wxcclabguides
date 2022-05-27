---
title: "Lab 1: Control Hub And Admin Portal"
---

### Overview of the lab:

In this Lab, we will go through the tasks that are required to complete the onboarding of a tenant. These tasks are to be undertaken by a customer administrator. By following each of the steps, you would have prepped your tenant to begin configuring different services offered by the platform. At the end of the lab, you should be able to login an agent with either the DN or the configured user extension.

# Table of Contents

- [Part 1: Control Hub OnBoarding Admin Tasks](#part-1-control-hub-onboarding-admin-tasks)
  * [1. Set Up Contact Center](#1-set-up-contact-center)
- [Part 2: Control Hub Calling Admin Task](#part-2-control-hub-calling-admin-task)
  * [1. Set Calling default Service Setting as Cloud Connected PSTN](#1-set-calling-default-service-setting-as-cloud-connected-pstn)
  * [2. Assign Numbers](#2-assign-numbers)
  * [3. Update Location and CCP](#3-update-location-and-ccp)
- [Part 3: Control Hub User Management Admin Task](#part-3-control-hub-user-management-admin-task)
  * [1. Add an admin user and configure the calling extension](#1-add-an-admin-user-and-configure-the-calling-extension)
  * [2. Add an agent user and configure the calling extension](#2-add-an-agent-user-and-configure-the-calling-extension)
  * [3. Add a supervisor user and configure the calling extension](#3-add-a-supervisor-user-and-configure-the-calling-extension)
  * [4. Add rest of the users](#4-add-rest-of-the-users)
- [Part 4: Admin Portal Multimedia Profile, Site and Team Configuration](#part-4-admin-portal-multimedia-profile-site-and-team-configuration)
  * [1. Create a new MultiMedia Profile](#1-create-a-new-multimedia-profile)
  * [2. Create a new Site](#2-create-a-new-site)
  * [3. Create a new Team](#3-create-a-new-team)
- [Part 5: Admin Portal User Configuration](#part-5-admin-portal-user-configuration)
  * [1. Synchronize Webex Contact Center Users](#1-synchronize-webex-contact-center-users)
  * [2. Manage settings for existing user](#2-manage-settings-for-existing-user)
  * [3. Login to the Agent Desktop](#3-login-to-the-agent-desktop)
- [Part 6: Tenant Creation Walkthrough](#part-6-tenant-creation-walkthrough)

# Introduction

### Lab Objective

- This lab is designed to ensure that you can begin customizing and configuring the call flows and various application services based on the customer requirements and business needs.
- The lab contains multiple exercises on Control Hub and Admin Portal to make you comfortable with the Webex Contact Center application. This lab will also help you in developing a familiarity with the control hub and admin portal UI.

### Pre-requisites

- You have an assigned POD
- You have the customer admin login credentials.
- You have the calling DNIS that should be assigned to the EntryPoint
- You have the extension number that should be assigned to each user

# Lab Section

## Part 1: Control Hub OnBoarding Admin Tasks

>The following video outlines the steps involved in the completion of tenant OnBoarding by the Customer Administrator. The objective of this lab is to make the customer admin trigger the background activities, that will complete the tenant setup. Skipping this step can cause social channels not to work.

<iframe width="560" height="315" src="https://www.youtube.com/embed/jU2RzlVFukg" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: https://admin.webex.com

### 1. Set Up Contact Center

- Login to Control Hub by accessing https://admin.webex.com
- Enter the admin email id and the password.
- Read & then Accept the Terms of Service by clicking the Accept button.
- Please familiarize yourself with the control hub UI by taking the tour of the UI
- Navigate to **_Contact Center_** Card
- Click on **_Settings_**
- Click on **_Set up Webex Contact Center_** and wait for the button to be greyed out.

## Part 2: Control Hub Calling Admin Task

>The following video outlines the Webex calling configuration steps that enable the administrator to use the configured default location and assign a number for those locations.

<iframe width="560" height="315" src="https://www.youtube.com/embed/stN4BoLDEBU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: https://admin.webex.com

### 1. Set Calling default Service Setting as Cloud Connected PSTN

- Login to Control Hub by accessing https://admin.webex.com
- Enter the admin email id and the password.
- Navigate to **_Calling Card_**
- Click on **_Service Settings_**
- Scroll down to **_PSTN Connection_** section
- Select **_Cloud Connected PSTN_**
- From the drop down, select **_IntelePeer_**
- Now hit **_Save_**

### 2. Assign Numbers

- Navigate to **_Locations_**
- Click on **_Richardson_** location to edit the location properties
- Click on **_Unassigned_** to set the PSTN Connection
- Click **_Edit_** under **_Local Gateway_**
- Hit **_Continue_** to **_Edit PSTN Connection for Richardson_**
- Select **_Cloud Connected PSTN_**
- From the drop down, select **_IntelePeer_**
- Check the 2 boxes for accepting **_Phone Number Porting Confirmation_**
- Click **_Save_** to finish the setup and then exit out of Location config pane

### 3. Update Location and CCP

- Navigate to **_Numbers_**
- Click on **_Add Numbers_**
- Under **_Location_** drop down , you should find **_Richardson_**. Select it
- Add the first DN and click on **_Validate_**
- Add the Second DN and click on **_Validate_**
- Click **_Save_**

## Part 3: Control Hub User Management Admin Task

>The following video outlines the process to manage different types of users to the Customer tenant. Following the steps, you will add admins, agents, and supervisors and also set each of their extension. While adding the user, we will see how to select user roles. Also, we will see how to change the user to an administrator for the customer tenant.

<iframe width="560" height="315" src="https://www.youtube.com/embed/-_wP9lwZbCE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: https://admin.webex.com

### 1. Add an admin user and configure the calling extension

- Navigate to **_Users_**
- Click on **_Manage Users_** button
- Click on **_Manually Add or Modify User_**
- Select **_Next_** in **_Manage Users_** pane.
- Input the **_EmailID_** of the admin user and click **_Next_**
- Verify that the **EmailID** is same as the one shared to you and click **_Next_**
- Check **_Webex Teams_** , **_Webex Calling (Enterprise)_** & **_Contact Center_**
- Ensure that the License Type is **_Premium Agent_** and Role is **_Agent_** and click click **_Add Users_**
- In the next page, enter the correct **_Extension_** under **_Assign Numbers_**. You can find this in the information already shared with you.
- Click **_Finish_**
- In the **_Users_** list, click on the recently added user to open the user modification card.
- Click **_Administrator Roles_**  under **_Roles and Security_**
- Select **_Organization Administrator (Full Administrator)_** and click **_Save_**
- If the user account has not been validated, check the email inbox and follow the instructions to validate the email account.

### 2. Add an agent user and configure the calling extension

- Navigate to **_Users_**
- Click on **_Manage Users_** button
- Click on **_Manually Add or Modify User_**
- Select **_Next_** in **_Manage Users_** pane.
- Input the **_EmailID_** of the admin user and click **_Next_**
- Verify that the **EmailID** is same as the one shared to you and click **_Next_**
- Check **_Webex Teams_** , **_Webex Calling (Enterprise)_** & **_Contact Center_**
- Ensure that the License Type is **_Premium Agent_** and Role is **_Agent_** and click **_Add Users_**
- In the next page, enter the correct **_Extension_** under **_Assign Numbers_**. You can find this in the information already shared with you.
- Click **_Finish_**
- If the user account has not been validated, check the email inbox and follow the instructions to validate the email account.

### 3. Add a supervisor user and configure the calling extension

- Navigate to **_Users_**
- Click on **_Manage Users_** button
- Click on **_Manually Add or Modify User_**
- Select **_Next_** in **_Manage Users_** pane.
- Input the **_EmailID_** of the admin user and click **_Next_**
- Verify that the **EmailID** is same as the one shared to you and click **_Next_**
- Check **_Webex Teams_** , **_Webex Calling (Enterprise)_** & **_Contact Center_**
- Ensure that the License Type is **_Premium Agent_** and Role is **_Supervisor_** and click **_Add Users_**
- In the next page, enter the correct **_Extension_** under **_Assign Numbers_**. You can find this in the information already shared with you.
- Click **_Finish_**
- If the user account has not been validated, check the email inbox and follow the instructions to validate the email account.

### 4. Add rest of the users

- Please follow the same steps as above to add any extra users that you want to add to the Contact Center.

## Part 4: Admin Portal Multimedia Profile, Site and Team Configuration

>The following video outlines how to access the admin portal and navigate the different configuration menus to create a Site, Team, and Multimedia Profile that will be assigned to each different Contact Center Users. We will also see how to navigate to Admin Portal from Control Hub UI

<iframe width="560" height="315" src="https://www.youtube.com/embed/c8po-wBO7Iw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: https://admin.webex.com

> Portal: https://portal.wxcc-us1.cisco.com/portal

### 1. Create a new MultiMedia Profile

- Login to Control Hub by accessing https://admin.webex.com
- Enter the admin email id and the password.
- Navigate to **_Contact Center_** Card
- Click on **_Settings_**
- Scroll down to **_Webex Contact Center Management_**
- Click on **_Go to Webex Contact Center Management Portal_**
- Ensure that browser pop up blockers are not blocking the **_Admin Portal_** pop up.
- Click on **_Provisioning_** and select **_Multimedia Profiles_**
- Click on **_+ New Multimedia Profile_** to open Multimedia Profile configuration page.
- Input Name as **_MM_Profile_wxcclab_** and input **_1_** for **_Voice_**, **_3_** for **_Email_** and **_3_** for **_Chat_** and click **_Save_**

### 2. Create a new Site

- Navigate to **_Provisioning_** and select **_Site_**
- Click on **_+ New Site_** button and provide the Name as **_Site_wxcclab_**
- Select **_MM_Profile_wxcclab_** in the **_Multimedia Profile_** drop down and hit **_Save_**

### 3. Create a new Team

- Navigate to **_Provisioning_** and select **_Team_**
- Click on **_+ New Team_**
- Select **_Site_wxcclab_** from the Site drop down
- Input Name as **_Team_wxcclab_**
- Select **_MM_Profile_wxcclab_** in the **_Multimedia Profile_** drop down and hit **_Save_**

## Part 5: Admin Portal User Configuration

>The following video outlines how to configure the users in Admin Portal that were added first in Control Hub. This is a very critical task from the Contact Center perspective. We also would take a look at how to associate customer-created Site, Team, and Multi-Media Profile with those users. Post this we should be able to successfully login as an agent using any of the users and their associated extension.

<iframe width="560" height="315" src="https://www.youtube.com/embed/MIpJofmfWKc" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub: https://admin.webex.com

> Portal: https://portal.wxcc-us1.cisco.com/portal

> Desktop: https://desktop.wxcc-us1.cisco.com/

### 1. Synchronize Webex Contact Center Users

- Login to Control Hub by accessing https://admin.webex.com
- Enter the admin email id and the password.
- Navigate to **_Contact Center_** Card
- Click on **_Settings_**
- Click on **_Synchronize Users_**

### 2. Manage settings for existing user

- Scroll down to **_Webex Contact Center Management_**
- Click on **_Go to Webex Contact Center Management Portal_**
- Ensure that browser pop up blockers are not blocking the **_Admin Portal_** pop up
- Click on **_Provisioning_** and select **_Users_**
- Click on **_..._** for the first user, to launch the **_Edit_** view for a particular User configuration
- Ensure that **_Administrator Profile_** is selected in the **_User Profile_** drop down.
- Click on **_Contact Center Enabled_** Toggle to move it to **_On_**
- In the **_Agent Settings_** section, select **_Site_wxcclab_** in the Site drop down
- Click in the **_Teams_** area and select **_Team_wxcclab_**
- Select **_MM_Profile_wxcclab_** in the **_Multimedia Profile_** drop down and hit **_Save_**
- Repeat the same for **_all other users_** by selecting the appropriate profile in the **_User Profile_** drop down

### 3. Login to the Agent Desktop

- Navigate to **_https://desktop.wxcc-us1.cisco.com/_** in a new browser tab
- Enter the agent's **_LoginID_** which could be found in the information shared with you.
- Enter the **_Password_** for the appropriate Login ID
- In the **_Station Login_** pane, Select **_Extension_** and input the configured _Extension_ for that user
- Click **_Submit_**. Ideally the login process should complete and you should now be successfully logged into **_Agent Desktop_**

## Part 6: Tenant Creation Walkthrough

>The following video does a quick demo on how a partner creates a tenant using the partner portal. This particular section is not part of the lab but is included as bonus content so that you get familiarized with this process. This also highlights the various configuration options that should be selected before the last step is executed which  is to click the Setup Webex Contact Center button.

<iframe width="560" height="315" src="https://www.youtube.com/embed/HkIDvYS3Lw8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Changelog:

| **Version** | **Comments**      | **Author(s)**                    | **Date**    |
| ----------- | ----------------- | -------------------------------- | ----------- |
| 1.0         | Initial Release   | Raghu Krishnan (rakrish2) | 08 Jan 2021 |
