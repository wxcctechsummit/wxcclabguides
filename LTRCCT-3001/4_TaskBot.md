---
title: 'Lab 4: Creating a Task Bot'
---

# Table of Contents
- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
  - [Tools we will be using](#tools-we-will-be-using)
  - [Use Cases](#use-cases)
  - [Vocabulary](#vocabulary)
  - [Accessing the Bot Builder](#accessing-the-bot-builder)
  - [Creating a Task Bot](#creating-a-task-bot)
  - [Editing the Flow to use your bot](#editing-the-flow-to-use-your-bot)
  - [Training](#training)
      - [Creating Entities](#creating-entities)
      - [Creating an Intent](#creating-an-intent)
  - [Creating Responses](#creating-responses)
  - [Launch Flow Builder](#launch-flow-builder)
    - [Congratulations, you have completed Lab2 tasks!](#congratulations-you-have-completed-lab2-tasks)


# Introduction
In this lab we will be creating a task bot using the bot builder in Webex Connect. We will collect information from the customer and either action it directly via API or pass the information to our chat agent so that they can assist our customer.  There are two paths that you can take to accomplish our use cases; using python or using the flow bulder.

---


## Tools we will be using
- Postman
- Bot Builder
- requestcatcher.com
- jsonpathfinder.com
- mockapi.io
- Webex Connect Flow Builder


## Use Cases
1. Check if an item is in stock
2. Change my order
3. Check shipping status 

## Vocabulary 
- Intents - Triggers that you bot will respond to
- Utterances - Training phrases that will map to Intents
- Entities - A kin to variables for running tasks. 
- Responses - Follow up to either get additional information regarding an entity or a response to an intent. 

## Accessing the Bot Builder 
- In the connect portal (https://cl2podXX.imiconnect.io)
- Click App tray <img src="images\Lab4_Apptray.PNG" height="20">
- Select Bot Builder <img src="images\Lab4_BotBuilder.PNG" height="20">
## Creating a Task Bot
- Select the Task bots option at the top of the screen
- Click the new Task Bot button
- Give the bot a name
- Click done

## Editing the Flow to use your bot


## Training
- Click Training <img src="images\Lab4_Training_menu.PNG" height="25">
#### Creating Entities 
- Select Entities
- For Each Entity:
  - Click Create Entity
    > Name: 
    >
    > Entity Type:
    >
    
    ---

#### Creating an Intent
- Select Intents
- Click Create Intent
  - 
- Add uterances 
  > Create a phrase similar to what a user might enter.
    >
    > Click link entity
    >
    >
    >

    ---

## Creating Responses
-  Click Responses <img src="images\Lab4_responses_menu.PNG" height="25"> 


## Launch Flow Builder 
- 







---

### Congratulations, you have completed Lab2 tasks! 

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/3.2_QnABotFlowConfig.html";}
function nextLab() 
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/5_CCAI.html";
 }
</script>

<div id="button-row">
<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go to the Previous Lab</button>

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go to the Next Lab</button>

</div>