---
title: "Lab 1d: # Connect overview"
---

# Table of Contents

- [Overview steps of IMI Connect](#overview-steps-of-imi-connect)
  * [1. Services](#1-services)
  * [2. Reports](#2-reports)
  * [3. Assets](#3-assets)
  * [4. Tools](#4-tools)
  * [5. Debug](#5-debug)
  * [6. Help](#6-help)
  * [7. App Tray](#7-app-tray)
  * [8. Settings](#8-settings)


# Introduction

The task of that lab is to introduce the IMI Connect interface which is used for the configuration of digital channels. In this lab you will not find configuration steps, the goal is to understand the purpose of each menu. It is designed only for introduction, as the result, you will learn each item in the menu.



# Overview steps of IMI Connect
> This is the introduction video. It walks through the menu items and explains the purposes of each tab.
<iframe width="1024" height="500" src="https://www.youtube-nocookie.com/embed/XXXX?rel=0" title="Lab  1d:Connect overview" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



## 1. Services

- Click on the `>>` icon in the left bottom of the menu, this will add the description of each item in IMI connect menu.

- Let's start with the Service. Create your own service by clicking on **SERVICES** > **CREATE NEW SERVICE** button. Please set the **SERVICE NAME** as `DEMO_Service`

- You will be redirected to your service configuration. In the **DASHBOARD** tab, at the right bottom, you can see the traffic statistic per each channel, flow execution, and Messaging API statistic.

- Click on a second tab **FLOWS** to see the list of all flows created for that service. You should not have any pre-built services right now.

- Click on the **RULES** tab to see which triggers are configured for which flows. Again, there are no triggers right now.

- Click on **API** tab. Here you can get the **SERVICE ID** and **SERVICE SECRET** which are needed for external applications which are using API.

- Click on the **SETTINGS** tab. Here you can rename or delete the service. 

## 2. Reports

- Click on the next item in menu **REPORTS** for generating a report based on the existing service. Select your service in **ENTITY** > **Live Chat** as channel > **Last 30 days** and click on the "GET REPORTS" button. Since there is no data, you will get a "No records found." message.

- Since that is a new Service, you should not see any statistics. You will get a _"No records found."_ message. Later you can find here such data as numbers of Submitted, Rejected, Delivered, Read, and Failed messages.

## 3. Assets

- Go to the next item in menu **ASSETS** > **Numbers**. This will show you the list of SMS numbers added to the platform.

- Now click on **ASSETS** > **Apps**. Here you will be able to configure later new applications such as "Email", "Messenger" (FaceBook), "Mobile/ Web" (Live Chat).

- Click on next item **ASSETS** > **Integrations** to see the list of all integrations configured for different events. By default, you should see only 2 Prebuilt Integrations.


## 4. Tools

- Click on **TOOLS** > **Download SDKs**. Here you can download SDK if you want to build your own application.

- Go to **TOOLS** > **Templates**. Here you can create a new template for one of 4 existing channels.

- Now, switch to **Export Logs** in the same **TOOLS** menu. This option will be needed during email configuration. You may also use it during troubleshooting.

- While you are in **Export Logs**, in the **Inbound Logs** section select your service name, Channel Event, time period, and click **DOWNLOAD** button.


## 5. Debug

- Go to **DEBUG** which is the next menu item. Debug Console used for troubleshooting purposes of the Flow. 

- In the **Historical Log** section, select the query Channel type and date range. Click on the **SEARCH** button and check if you have any data.


## 6. Help

- Go to the next menu item by clicking on **HELP** > **Documentation** which redirects to the IMI documentation portal. All menu items are documented in that documentation.

- Go to the second item in the **HELP** menu by clicking on **API Reference**. This will forward you to the API documentation portal.

- Now switch to the **Change Log** item in the same menu. Here you can find the updates of the product.


## 7. App Tray

- Click on the **APP TRAY** > **Bot Builder**. Application Tray allows running a Bot Builder tool where you will create the bot in one of the next tasks.

## 8. Settings

- Click on the next item **Settings** > **Profile Settings** and check the Profile settings.

- Go to **SETTINGS** > **Tenant Settings** and verify the configured Time Zone and Date Format.

- Open **SETTINGS** > **Usage** to see the general statistic of the entire tenant.

- Click on the next item **SETTINGS** > **Contact Support**. Here you can check the details of support email IDs.

- Click on the next item **SETTINGS** > **Teammates**. From here you can add more users to IMI Connect or change the permissions for existing users.

- Go to **SETTINGS** > **Groups/Teams** where you can create a new group or team. Please refer to _"here"_ link to see the explanation of Groups and Teams.

- As the final step click on the **Logout** in the **SETTINGS** menu and make sure that you are signed out from the IMI Connect.


### Congratulations, you have completed this section. Well done!!!
