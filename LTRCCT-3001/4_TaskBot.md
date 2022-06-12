---
title: 'Lab 4: Task Bot Flow Modification'
---

# Table of Contents
- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
  - [Accessing the Bot Builder](#accessing-the-bot-builder)
  - [Creating a Task Bot](#creating-a-task-bot)
  - [Editing the Flow to use your bot](#editing-the-flow-to-use-your-bot)
  - [Decide between Code or Flow Builder for actioning bot logic.](#decide-between-code-or-flow-builder-for-actioning-bot-logic)


# Introduction
In this lab we will be creating a task bot using the bot builder in Webex Connect. We will collect information from the customer and either action it directly via API or pass the information to our chat agent so that they can assist our customer.  There are two paths that you can take to accomplish our use cases; using python or using the flow bulder.

---



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
- Click on the service that you created
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

- Open the Recieve Node
- Click on Transaction Actions:

    > Add Action
    >
    > Time: On-Leave
    > 
    > Action: Set Variable
    >
    > Variable: message
    >
    > Value: Output Varriables > InApp - Form Response > inappmessaging.message $(n38.inappmessaging.message)
    >

    ---

- Add Task Bot node <img src="images\Lab4_TaskBot.PNG" height="25"> over top of the existing Queue Task node
-Find the Create Task node and click on the green line that says created, which connects to the queue Task node. Click on it and delete it.
- Click and drag from the green node edge to the Task Bot node 
    > <img src="images\Lab4_Connect_Task_Node.gif">


- Open the Task Bot node by double clicking
    > Bot: your task bot
    >
    > Message: Custom Variables > messageForBot $(messagetext)
    >
    > Channel: In-App
    >
    > Unique ID: Custom Variables > conversationId $(conversationId)
    >
    > Click Customer Parameters
    >
    > Key: name
    >
    > Value: Recieve > inappmessaging.formFields.Name
    >

    ---

- Add Live Chat or In-App Messaging Node <img src="images\Lab4_In-App.PNG" height="25"> next to the Task Bot node
- Drag the green node edge from taskbot to the Live Chat or In-App Messaging Node
  - Select onSuccess and press OK
- Drag the green node edge from taskbot to the Queue Task Node
  - It will automatically create the connection for onAgentHandover
- For each Red and Orange node edge on the Task Bot Node
  - Drag the node edge connector to the Close Conversation node until you can no longer grab any new node edges.
- Open the Live Chat or In-App Messaging Node
    > Destinaton Type: UserId
    >
    > Destination Type: Start > inapppessaging.userId $(n2.inappmessaging.userId)
    >
    > Message: Task Bot > taskbot.text_response $(n2303.taskbot.text_response)
    >
    > Thread ID: Start > inappmessaging.threadId $(n2.inappmessaging.threadId)
    >
    > Click Save

    ---

- Add Append Conversation Node <img src="images\Lab4_Append.PNG" height="25">
  - Drag the green node edge from the Live Chat or In-App Messaging Node and connect it to the Append Conversation Node
  - For each Red node edge on the Task Bot Node
    - Drag the node edge connector to the Close Conversation node until you can no longer grab any new node edges.
- Open the Append Conversation Node
    
	> Method Name: Append Chat
	>
	> Node Runtime Authorization: Pick default
	>
    > Channel: Livechat
    >
    > Conversation ID: Custom Variables > conversationId  $(conversationId)
    >
    > Message Type: Text With Attachments
    >
    > Direction: Outbound
    >
    > Text: Task Bot > taskbot.text_response $(n2303.taskbot.text_response)
    >
    > Timestamp: Start > inappmessaging.timestamp $(n2.inappmessaging.timestamp)
    >
    > Attachments: null
    >

	---

- Add a Recieve Node <img src="images\Lab4_Recieve.PNG" height="25">
- Drag the green node edge from the Append Conversation Node and connect it to the Recieve Node
  - For each Red or Orange node edge on the Append Conversation node
    - Drag the node edge connector to the Close Conversation node until you can no longer grab any new node edges.
- Open the Recieve Node
	> Select Incomming Message/Event: Recieve In-App Messaging   
	>
	> Max timeout: 300
    >
    > From(threadID): Start > inappmessaging.threadId $(n2.inappmessaging.threadId)
    >
    > From(userId): Start > inappmessaging.userId $(n2.inappmessaging.userId)
    >
    >Event name: Incoming Message
    >
- Click on Transaction Actions:

    > Add Action
    >
    > Time: On-Leave
    > 
    > Action: Set Variable
    >
    > Variable: messagetext
    >
    > Value: Output Varriables > inappmessaging.message $(n2311.inappmessaging.message)
- Click Save  
- For each Red or Orange node edge on the Recieve Node
    - Drag the node edge connector to the Close Conversation node until you can no longer grab any new node edges.

	---


- Add Append Conversation Node <img src="images\Lab4_Append.PNG" height="25">
- Drag the green node edge from the Recieve Node and connect it to the Append Conversation Node

	- Open the Append Conversation Node
    
	> Method Name: Append Chat
	>
	> Node Runtime Authorization: Pick default
	>
    > Channel: Livechat
    >
    > Conversation ID: $(conversationId)
    >
    > Message Type: Text With Attachments
    >
    > Direction: Inbound
    >
    > Text: messagetext $(messagetext)
    >
    > Timestamp: Start > inappmessaging.timestamp $(n2.inappmessaging.timestamp)
    >
    > Attachments: null
    >
  
- Drag the green node edge from the Append Conversation Node and connect it to the Task Bot Node
  - For each Red or Orange node edge on the Append Conversation Node
    - Drag the node edge connector to the Close Conversation node until you can no longer grab any new node edges.
     
	---

- Save the Flow
- Click Make Live
- Select your Application and add any publish comments 


## Decide between Code or Flow Builder for actioning bot logic.

<script>
function code() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/4_TaskBot_Code.html";
}
function flowBuilder() {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/4_TaskBot_Flow.html";
 }
function previous() {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/3.3_QnABotAdvanced.html";
 }

</script>

<div id="button-row">
<button onclick="code()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Code</button>
Or 
<button onclick="flowBuilder()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Flow Builder</button>

</div>

<div>
<button onclick="previous()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go to the Previous Lab</button>
</div>