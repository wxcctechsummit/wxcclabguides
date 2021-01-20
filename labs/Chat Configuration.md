# Chat Configuration

Part 1 : 

Video example

<iframe width="560" height="315" src="https://www.youtube.com/embed/PsK4DqSgtb8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


# Introduction

## Lab Objective

This lab is designed to guide for creating Entry Point/Queue/MultimediaProfile entities, used in chat configuration on WxCC.   

We will be configuring Entry Point, Queue, Multimedia Profile. 

## Pre-requisites

1. Portal URL.
2. Admin credentials to configure

### 1. Chat Entry Point creation

• Customer admin logs in to “CJP Management Portal” URL https://portal.cjp.cisco.com  with the credentials and accesses the menu 'Provisioning -> Entry Point/Queues -> Entry Point'.
• Select “New Entry Point” and enter the respective values and click save.

### 2. Chat Queue creation

• Customer admins accesses the menu 'Provisioning -> Entry Point/Queues -> Queue'.
• Select “New Queue” and enter the respective values and click save.

### 3. Multimedia Profile creation

• Customer admins accesses the menu 'Provisioning -> Multimedia Profiles -> New Multimedia Profile'.
• Enter the respective values and click save.




Part 2 :

Video example

<iframe width="560" height="315" src="https://www.youtube.com/embed/WGjbBwupBx0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents

1. Assign team
2. Setup chat template
3. Entry point routing strategy creation
4. Queue routing strategy creation

# Introduction

## Lab Objective

This lab is designed to guide chat template configuration on WxCC.   


## Pre-requisites

1. Portal URL.
2. Admin credentials to configure.

### 1. Assign the team setup to handle chat, to the user.
. Customer admin logs in to “CJP Management Portal” URL https://portal.cjp.cisco.com  with the credentials and accesses the menu ‘Provisioning -> Users'.
. Select 'Users' and edit the user to assign the specific team to the user. 
. click save.

### 2. Chat template creation
. Customer admin logs in to “CJP Management Portal” URL https://portal.cjp.cisco.com  with the credentials and accesses the menu ‘Provisioning -> Users'.
. Customer admin launches Control Hub by clickiing on Hypertext link "Cisco Webex Control Hub" present on the users module. 
. Provide the same email as provided at the time of login to “CJP Management Portal” URL https://portal.cjp.cisco.com, when prompted at Control Hub login page.
. From the left hand side menu select "Contact Center" -> select "Features" option from the top right options.
. Select "New" -> "Chat Template" -> "Enter a name for you to identify this template" -> Select the preconfigured entry point -> Click the blue arrow icon on right to go to next page.
. Under "Template Overview" select the requisite options to design customer side chat window preview-> Click the blue arrow icon on right to go to next page.
. On "customer information" page select the requisite options to design the customer side chat window preview -> Click the blue arrow icon on right to go to next page.
. Select the requisite attributes to create the "Off-Hours" customer side chat window preview -> Click the blue arrow icon on right to go to next page.
. Select the requisite attributes to design the Feedback preview, this screen is used to collect feedback from a customer after the chat ends -> Click the blue arrow icon on right to go to next page.
. On "Branding and Identity" page select the requisite attributes to setup customer side chat window preview -> Click the blue arrow icon on right to go to next page.
. On "Status Messages" page configure the status messages to display in the customer chat window for different statuses "Waiting/Chatting/Left the Chat" -> Click the blue arrow icon on right to go to next page.
. Click on Finish to complete the setup.
. Select "Download Embed Code" option to save the Chat_Code_Snippet. This can used to launch the chat from any JS editor.


### 3. Entry point routing strategy creation

• Customer admins access the menu and clicks ‘Routing Strategy’ which cross launches the routing strategy page.
• Select the ‘chat entry point’ that you created from the drop down and click on ‘New Strategy’ button.
• Enter the Routing strategy name.
• Assign the chat queues and save.


### 4. Queue routing strategy creation

• Now from the routing strategy page, select the ‘queue’ that you created and click on ‘New Strategy’ button.
. Enter the Routing strategy name and select the ‘Routing Type’ from the drop down.
• Enter the 'Time Settings', 'Advanced settings' and 'Chat Distribution’ by selecting 'Add Group'.
• Select the Team to which the contact should be delivered and click save group.
• Now click save to complete Queue routing strategy settings. 









