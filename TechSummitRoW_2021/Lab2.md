---
title: 'Lab 2: Agent and Supervisor Desktop'
---

# Working With Custom Desktop Layouts

Video example

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/ZYFwqEjZLWM?rel=0" title="WxCC Customizing Agent Desktop Lab" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents

- [1. Agent Desktop](#1-download-default-desktop-layout)
  - [1.1. Create Customized Desktop Layoute](#2-customize-default-desktop-layout-with-logo-and-title)
  - [1.2. More Advance Customized Desktop Layout](#3-upload-the-custom-desktop-layout-an-verify)
- [2. Supervisor](#4-assign-header-widget-and-nav-bar-widget)
  - [2.1. Portal's Dashboards](#5-upload-the-modified-layout)
  - [2.2. Permissions and Remote Agent Logout](#6-verify-the-layout)

# Introduction

## Lab Objective

The object of this lab excercise is to customize the logo and title of the agent desktop and also add widget in the header section and nav bar section.

## Pre-requisite

1. Administrator/ Supervisor with portal access​.
2. New user (Agent) is already created​.
3. Agent is able to login to agent desktop​.
4. Agent should be part of a team​.
5. Basic knowledge of JSON format​
6. Use any online [JSON validator](https://jsonlint.com) to validate the file​

## Quick Links

- <a href="https://portal.wxcc-us1.cisco.com/portal" target="_blank">Portal</a>
- <a href="https://analyzer.wxcc-us1.cisco.com/analyzer/home" target="_blank">Analyzer</a>
- <a href="https://desktop.wxcc-us1.cisco.com" target="_blank">Agent Desktop</a>

### 1. Download default desktop Layout

- Login to [WxCC portal](https://portal.cjp.cisco.com/portal/home.html) with admin credentials​
  - Note that you should have at least one agent configured for testing at this point
- Navigate to Provisioning --> Desktop Layout​
- Click on ellipses `...` of Global Layout to edit [Video Direct Link](https://www.youtube.com/embed/ZYFwqEjZLWM?start=150)
- Now click on edit
- Click on download button ​
- Download the Default Desktop Layout.json file​
- Now cancel out, as you only need to get the JSON file

### 2. Customize default desktop layout with logo and title

- Open the Default Layout JSON in any text editor e.g. Notepad or Sublime text.​
- Modify the value of appTitle key to change Agent Desktop title ​
- Modify the value of logo key as your company logo URL or use this dummy url: https://widget-kad.s3.amazonaws.com/Logos/boscologo5.png
- “Save As” the JSON file with a distinguishable name.

### 3. Upload the custom desktop layout an verify

- Login to [WxCC portal](https://portal.cjp.cisco.com/portal/home.html) with admin credentials​
- Navigate to Provisioning --> Desktop Layout​
- Click on New Layout
- Provide any preferable name and description ​
- Click on Team textbox to add the team ​
- Click Upload button to upload the modified JSON file​
- Click Save button to apply the layout.
- Login/Reload [WxCC agent desktop](https://desktop.wxcc-us1.cisco.com) to verify the layout

### 4. Assign header widget and nav bar widget

- Open the layout JSON file in any text editor e.g.
- Notepad or Sublime text.(be careful copying from PowerPoint might add unwanted spaces/characters... causing the JSON to \* \* fail on load) use an online [JSON formatter](https://jsonformatter.org/) to clean up if required.​
- Modify the header section as mentioned in video
- Modify the navigation section by creating a new navigation widgit with a direct link​ [Video Direct Link](https://www.youtube.com/embed/ZYFwqEjZLWM?start=330)
- “Save As” the JSON file with a unique preferable name

### 5. Upload the modified layout

- Login to [WxCC portal](https://portal.cjp.cisco.com/portal/home.html) with admin credentials​
- Navigate to Provisioning --> Desktop Layout​
- Search for your layout ​
- Click on ... to edit the existing layout​
- Now click on edit
- Click Upload button to upload the modified JSON file​
- Finally click Save button to apply the layout.

### 6. Verify the layout

- Login/Reload [WxCC agent desktop](https://desktop.wxcc-us1.cisco.com) to verify the layout



## 1. Agent Desktop

## 1.1: Create a Custom Desktop Layout

> Watch the following video to learn the dekstop layout customization process. After the video, you will be able to customize the Agent Desktop with your company logo and you will see a more advanced and cool layout example.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/CRoZlFAS49I?rel=0" title="WxCC Lab #2 Part 4: Custom Desktop Layout" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 1. Download default desktop Layout

- Login to **[https://portal.wxcc-us1.cisco.com](https://portal.wxcc-us1.cisco.com){:target="_blank"}** with admin credentials.

- Navigate to **_Provisioning_** –> **_Desktop Layout_**.

- Click on ellipses `...` of Global Layout and select **_Edit_**.

- Click on **_Download_** button to download the **Default Desktop Layout.json** file.

### 2. Customize default desktop layout with logo and title

- Open the **Default Desktop Layout.json** file with any text editor (e.g. Notepad or Sublime text).

- Modify the **_appTitle_** key value with your company name in order to change Agent Desktop title.

- Modify the **_logo_** key value with your company logo URL or use this **https://raw.githubusercontent.com/wxcctechsummit/holcct2100/main/labslive/CiscoLiveLogo.jpg**.

- **_Save As_** the JSON file with a distinguishable name.

### 3. Upload the custom desktop layout and associate it to a team

- Go as admin to **_Desktop Layout_** module in the **[Tenant Portal](https://portal.wxcc-us1.cisco.com){:target="_blank"}**.

- Click on **_New Layout_**.

- Provide the preferable **name** `Custom Desktop Layout <ID>`. Your \<ID\> is provided in the email in the **"Attendee ID"** line.

- Select `Team2_wxcclab_<ID>` as Team.

- Click **_Upload_** button to upload the modified JSON file.	

- Click **_Save_** button to apply the layout.

### 4. Verify the new custom desktop layout

- Login in the **[Agent Desktop](https://desktop.wxcc-us1.cisco.com/){:target="_blank"}**.

- Open the **_User Profile_** and click on the arrow `>` under **_Team_**.

- Change the team of the agent to `Team2_wxcclab_<ID>`.

- Click on **_Save Team Selection_**.

- Confirm the changes by clicking on **_Change Team_**.

- Wait some seconds to see the results. Now you should get a new log icon in the left upper corner.


## 1.2: More advance example

### 1. More advance example

- Download the **[custom JSON file](https://cisco.box.com/s/4hmozg4h9gwaa1x9zhq1w6mehw8guvuy){:target="_blank"}**.

- Go again to **_Desktop Layout_** module in the **[Tenant Portal](https://portal.wxcc-us1.cisco.com){:target="_blank"}**.

- Click on **_New Layout_**.

- Provide any preferable **name and description**.

- Select `Team1_wxcclab_<ID>` again as Team.

- Click **_Upload_** button to upload the modified JSON file.

- Click **_Save_** button to apply the layout.

- Go back to the **[Agent Desktop](https://desktop.wxcc-us1.cisco.com/){:target="_blank"}** and change the team to `Team1_wxcclab_<ID>`.

- **See** the new desktop layout.


>The following video outlines the existing dashboards available to the supervisor in the management portal. Follow the instructions to find out which dashboards are available and what they are for.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/E5IQn55aFmM?rel=0" title="WxCC Lab #5 Part 1: Portal Dashboards" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## 2: Supervisor

## 2.1: Portal's Dashboards
 
### 1. Management Portal with Supervisor account

- Make sure the agent is logged into the agent interface **[https://desktop.wxcc-us1.cisco.com/](https://desktop.wxcc-us1.cisco.com/){:target="_blank"}** 

- Make the agent **Available** by selecting the appropriate state in the upper left corner.

- Navigate to **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}** in a new browser tab

- Enter the suprvisor’s **Username** which you created in the first lab.

- Enter the **Password** for the appropriate Username.

### 2. Portal's dashboards information

- Ensure that browser pop up blockers are not blocking the **_Admin Portal_** pop up. The `Entry Point - Site level` dashboard has to be shown on the landing page.

- Make sure there are more than 0 agents listed in the **AVAILABLE AGENTS** field.

- Make a new call to your EP. After starting IVR, you will see this value in the **IN IVR** field.

- Now redirect your call to the queue with the agent. Make sure the agent answered this call. You should see a value of 1 in the **CONNECTED** field. 

- Navigate to the agent desktop, end your call and move your agent back to the **Idle** status. Nobody should be in **Available** status.

- Go back to the portal's dashboard and select the second dashboard `Contact Center Overview - Realtime` in the upper left corner.

- Make a new call to your EP and wait until the call reach a queue.

- Check the new data on the Realtime dashboard. Now, this call will be presented in the table **Contact Details in the Queue**. In addition, the value will increase in the **Longest Contact Currently in Queue** chart.

-  Select the third dashboard `Contact Center Overview - Historical`. You will be able to see the same information but from the historical perspective. By default the informaiton is shown for the last 7 days. Change the **Duration** filter to **This Year** in the upper right corner. 

- Open the help guide by clicking on the supervisor account in the upper right corner and selecting the **Help** option.

## 2.2: Supervisor permissions and remote agent logout

>Here we go through the newly added dashboard. We will learn how to change supervisor permissions and how to manually log out agents by using a supervisor account.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/nseNRPTL7Ag?rel=0" title="WxCC Lab #5 Part 2: Supervisor permissions and remote agent logout" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 1. Agent State Data – Realtime dashboard 

- Make sure that the agent is logged in.

- Go to the portal's dashboard as a supervisor and select the 4th dashboard `Agent State Data – Realtime` in the upper left corner.

- Now the agent has to be presented in the **Agent State Data** dashboard.

- Manually refresh dashboard data by clicking on **Stop Refresh** button. As the result, the **time since last refresh** will be restarted.

### 2. Remote Agent Logout 

- To log out an agent, click **Sign Out** button in the **Action** column. 

- Make sure that you receive a notification that the agent has been successfully logged out.

> **Note:** You can log out agents who are in the Available, Idle, or Not Responding. If the agent is in a **Connected** state the Sign Out button will not be available.

- Go to the Agent desktop and verify the agent status. He should receive the notification that the supervisor has signed him out.

| **Entity** | **Name**      | 
| ----------- | ----------------- | 
| User Profiles        | Supervisor Profile \<ID\>   | 
| Supervisor         | supervisor1_\<ID\>@mailinator.com | 

> **NOTE:** Your \<ID\> is provided in the email in the **"Attendee ID"** line.

### 3. Supervisor’s User Profile

- Make sure the agent is logged back into the agent interface. During the agent login select the `Team2_wxcclab_<ID>`.

- Navigate to **_Provisioning_** and select **_User Profiles_**.

- Click on dots `...` infront of **_Supervisor Profile_** and select **Copy** option.

- The new **User Profile** page will be presented. Set the **Name** base on your Attendee \<ID\> `Supervisor Profile <ID>`.

- In the **User Profile** page click on **Access Rights**.

- In **Teams** field set only team1 `Team1_wxcclab_<ID>` and click **Save**.

- Navigate to **_Provisioning_**, select **_Users_** and modify your supervisor account.

- Click on **_Provisioning_** and select **_Users_**.

- Infront of the current supervisor `supervisor1_<ID>@mailinator.com` click on `...` , to launch the **_Edit_** view for a particular User configuration.

- Select a created profile `Supervisor Profile <ID>` in the **_User Profile_** drop down list and hit **_Save_**.

- Log out and log back in to apply the new supervisor profile settings.

- Verify that there are no agents in the `Agent State Data – Realtime` dashboard with a new profile.

- Go to the agent desktop and change the team settings. Switch the agent to the team1 `Team1_wxcclab_<ID>`.

- In the agent dashboard click the **_Stop Refresh_** button and make sure the agent appears.

[To top of this lab](#table-of-contents)




<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LabLibrarynew";}
function nextLab() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/labsnew/Lab3.html";}
</script>

<div id="button-row">	
<button onclick="mainPage()" style="border-radius: 5px;background-color: rgb(116,191,75);padding: 10px">Go back to Main Page</button>

<button onclick="nextLab()" style="position: absolute;right: 200px;border-radius: 5px;background-color: rgb(116,191,75);padding: 10px;">Next Lab 3: IVR and Contact Routing</button>

</div>
