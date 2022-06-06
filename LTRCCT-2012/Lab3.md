---
title: 'Lab 2: Menu & opt_Out'
---

# Table of Contents

- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
    - [Recap](#Recap)
    - [Lab Objective](#lab-objective)
    - [Pre-requisites](#pre-requisites)
    - [Quick Links](#quick-links)

- [Lab Section](#lab-section)
  - [Step 1. HTTP Node](#HTTP Node)
  - [Step 2. Agent Login](#AGent login)
  - [Step 3. Flow configuration  )](Flow configuration )



# Introduction

### Recap

 In the first 3 Lab, we Learned
 1. Map Dial number to Entry point and mapping flow Dial Number-->Entry Point --> Routing Point-->Flow , contact hear welcome message
 2. Connect contact to Agent Desktop
 3. provide Menu option and an Opt-Out options to customer and validate CallBack Functionality

### Lab Objective

In this section, we will go over the steps that are required to do External Data DIP. In this Lab you will learn the following
1. External Data Dip to 3rd party Web Services  
2. Parsing the JSON
3. Collect variable dynamically from WebServices and Display it on Agent Desktop



### Pre-requisites

- Basic IVR flow worked, caller can connect to WXCC and hear welcome music
- Caller Successfully connect to Agent Desktop
- Menu and Opt Out lab completed



### Quick Links

> Control Hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com](https://desktop.wxcc-us1.cisco.com){:target="_blank"}**\




# Lab Section

## Step 1. HTTP Node

>The HTTP Request activity fetches information from an external data source such as a CRM using standard HTTP protocols.
>Basic Auth and OAuth 2.0 attributes are supported for authenticated endpoints

The request we will construct is :

HTTPS GET -> https://5f97898842706e0016957443.mockapi.io/crm/api/customers?pin=18716

Use the variable from the CollectDigits1.EnteredPIN variable to inject it in the pin lookup.
We will construct it as follows
HTTP Request
GET https://5f97898842706e0016957443.mockapi.io/crm/api/customers

Query Parameters:
pin with  

with value of the block (recheck your block variable name!)

The type would be application/json

The Parse settings would be :
customerName = $.[0].name
customerEmail = $.[0].email
customerPhone = $.[0].phone
Tech-Tip: Here are some practice exercises you can try by going to jsonpath.com

Go to https://5f97898842706e0016957443.mockapi.io/crm/api/customers
Copy out the JSON into https://jsonpath.com on the left pane.

Try out all of these to learn how JSON path works!
|Query For |	Parse statement |
|----------|------------------|
|All Customers|	$.*|
|First Customer|	$.[0] |
|Last Customer|	$.[-1:]|
|First two customers|	$.[0:2]|
|Last two customers |	$.[-2:]|
|Second from last	|$.[-2:-1]|
|All the names|	$..name |
|All the pins	| $..pin |
|All the customers who’s pin value is more than 70000 or 80000 |	$..[?(@.pin > 70000)] |
|All details of customer with account number|	$..[?(@.account == "87305901”)].*|
|Name of customer with account number | 	$.[?(@.account == "70579265")].name|



## Step 2. Agent Login


## Step 3. Flow configuration

1. Copy the Lab1 flow by clicking on 3 dot
<img align="middle" src="Images/Lab2/Flow1.jpg" width="500" />

2. Remove Play message node
<img align="middle" src="Images/Lab2/Flow2.jpg" width="500" />

3. Drag and Drop Menu Node and connect NewPhoneContact node to MenuNode
<img align="middle" src="Images/Lab2/Flow3.jpg" width="500" />

4. i) Click on Menu node, rename it to ```MainMenu``` and

   ii) Select ```1_main_main.wav``` file

   iii) Add 3 custom menu link 1,2,3 and add respective Descriptions

   <img align="middle" src="Images/Lab2/Flow41.jpg" width="200" />
   <img align="middle" src="Images/Lab2/Flow42.jpg" width="200" />
   <img align="middle" src="Images/Lab2/Flow43.jpg" width="200" />


 <img align="middle" src="Images/Lab2/flow44.jpg" width="500" />

5. Drag and drop Queue contact node and select ```Dummy_Queue``` created

<img align="middle" src="Images/Lab2/selectqueue.jpg" width="500" />


6. To Set ```QueueCounter``` Variable

   i) Click anywhere on the Flow canvas

   ii)Click on ```Add Flow Variable```

   iii) Create a ```integer```variable named ```QueueCounter``` and set Default value to ```0```

   <img align="middle" src="Images/Lab2/Flow61.jpg" width="500" />
   <img align="middle" src="Images/Lab2/Flow62.jpg" width="500" />



7. Set ```QueueCounter``` variable
 i) Drag and Drop ```SetVarible``` node

 ii) In the variable select ```QueueCounter``` variable created

 iii) In the set value type ```{{QueueCounter+1}}```, Note: variable in the set node must always be typed inside ```{{}} ``` braces

 <img align="middle" src="Images/Lab2/Flow71.jpg" width="500" />



8. Drag and Drop ```PlayMusic``` node and select ```Music File``` and set ```offset``` to ```5```
  <img align="middle" src="Images/Lab2/Flow81.jpg" width="500" />

9. Drag and Drop ```Condition``` node and set the condition to  ```{{QueueCounter<2}}``` if ```True``` connect it to ```SetQCounter```

  <img align="middle" src="Images/Lab2/Flow81.jpg" width="500" />

10. Drag and Drop ```PlayMessage``` node and select  ```2_high_call_volume.wav``` file and connect ```False``` output to   ```PlayMessage```  node

  <img align="middle" src="Images/Lab2/Flow101.jpg" width="500" />

11. Drag and Drop ```Menu``` node and select  ```3_callback_menu.wav``` file and add  2 more custom links 1 and 2 for  ```callback``` and  ```Voicemail```  

    <img align="middle" src="Images/Lab2/Flow111.jpg" width="500" />

12. Set call back

i) Drag and Drop ```PlayMessage``` node and select  ```4_callback_confirm.wav``` file

ii) Drag and Drop ```Callback``` node and set  ```callback Dial Number``` to ```NewPhoneContact.ANI```  and ```Static Queue```  to the queue created in lab 1

iii) connect ```DisconnectContact``` node to callback node

  <img align="middle" src="Images/Lab2/Flow121.jpg" width="500" />

  <img align="middle" src="Images/Lab2/Flow122.jpg" width="500" />

13. Set Voicemail

i) Drag and Drop ```Blindtransfer``` node and set  ```Number``` to ```+18005532447``` which is Cisco  TAC support number

ii) Repeat the same for ```optout``` menu as well
 <img align="middle" src="Images/Lab2/Flow131.jpg" width="500" />

  <img align="middle" src="Images/Lab2/Flow132.jpg" width="500" />

14. Connect ```No-input Timeout``` and ```Unmatched Entry``` from Main menu to itself

15. Connect ```No-input Timeout``` and ```Unmatched Entry``` from OptOut menu to ```SetQCounter```  node

16. validate &  Publish the flow

<img align="middle" src="Images/Lab2/Flow151.jpg" width="500" />

<img align="middle" src="Images/Lab2/Flow152.jpg" width="500" />

17. Edit ```Current``` Routing Strategy and  change the flow to ```Lab2```

<img align="middle" src="Images/Lab2/Flow171.jpg" width="500" />

18. Validate the flow

i) To test the flow call the Dial Number configured and traverse through different menu and leave ```CallBack``` and make sure Agent get the call


### Dial the Number from your mobile phone and make sure to traverse through different menu and leave ```CallBack``` and ```Voicemail```



### Congratulations, you have completed Lab2 tasks!











---



<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/Home.html";}
function nextLab()
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/2_BasicChat.html";
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
