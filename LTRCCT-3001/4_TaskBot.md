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
  - [Decide between Code or Flow Builder for actioning bot logic.](#decide-between-code-or-flow-builder-for-actioning-bot-logic)


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
- Retun to Services
- click on the service that you created
- Click View My Flows
- Click Create Flow
  > Flow Name: give your task flow a name 
  >
  > Type: Work Flow 
  >
  > Method: Copy from existing flow 
  >
  > Select flow: your inbound chat flow
  > 
  > Click Create

  ---
- Open the first Recieve Node
- Click on Transaction Actions:

    > Add Action
    >
    > Time: On-Leave
    > 
    > Action: Set Variable
    >
    > Variable: messageForBot
    >
    > Value: Output Varriables > InApp - Form Response > inappmessaging.message
    >

    ---

- Add Task Bot Node

    > Bot: your task bot
    >
    > Message: Custom Variables > messageForBot $(messageForBot)
    >
    > Channel: In-App
    >
    > Unique ID: Custom Variables > conversationId $(conversationId)
    >

    ---

- Add Live Chat or In-App Messaging Node

    > 
    >
    >
    >
    >

    ---

- Add Append Conversation Node

	>
	>
	>
	>

	---

- Add a Recieve Node

	>
	>
	>

	---


- Add Append Conversation Node

	>
	>
	>
	>

	---


- Add Live Chat or In-App Messaging Node for error handeling

	>
	>
	>
	>

	---


## Decide between Code or Flow Builder for actioning bot logic.
- [Code]([4_TaskBot_Code.md](https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/4_TaskBot_Code.html))
- [Flow Builder]([4_TaskBot_Flow.md](https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/4_TaskBot_Flow.html))










