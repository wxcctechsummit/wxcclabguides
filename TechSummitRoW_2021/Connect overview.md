---
title: "Lab 1d: # Connect overview"
---

# Table of Contents

- [Introduction to the New Webex CC APIs](#part-1-introduction-to-the-new-webex-cc-apis)
  * [1. Walkthrough of Auth Flow](#1-walkthrough-of-auth-flow)
  * [2. Initial Setup of Sample App](#2-initial-setup-of-sample-app)

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

- 



### Congratulations, you have completed **ALL section**. Well done!!!
### We would like to keep track of your progress and make sure that we are giving you effective support. Please take approximately one minute to complete the short survey.

<script>
function celeButton() 
	{
	window.open("https://app.smartsheet.com/b/form/42c2c1f4e71940088ad0ea8053ac3006", '_blank');
	document.body.style.backgroundImage="url('https://media.giphy.com/media/PMV7yRpwGO5y9p3DBx/giphy.gif')";
	}
</script>

<div id="button-row">
	<button onclick="celeButton()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Take Survey and Finish Labs</button>
</div>

<br />
<br />
&nbsp;
&nbsp;
