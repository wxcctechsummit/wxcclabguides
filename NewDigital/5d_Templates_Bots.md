---
title: 'Lab 5d: Associate bot in FBM Flow'
---

<iframe width="1024" height="576" src="https://www.youtube.com/embed/GzWhZUtpohw" title="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents

- Lab 5d- Associate bot in FBM Flow
    * Bot and agent escalation explained
    * Update the FBM Inbound workflow

# Introduction

## Lab Objective
This lab is designed to complete the integration of the QnA bot with the Facebook Messenger channel.

## Pre-requisite
- WxCC Portal, Agent Desktop and IMI connect URL
- Admin credentials to complete configurations in WxCC portal and IMI connect
- Agent Credentials to Handle FBM digital contact
- Basic FBM contact routing should be working
- QnA bot created and live

## Lab 5b - Task Bot Creation

### 1. Bot and agent escalation explained
- Incoming message from customer is set to a variable called `messagetext`

- This message from cusotmer is sent to bot 

- The bot sends `qnabot.text_response` back to the caller

- The outbound message is using the `Append Conversation node`

- We are receiving the message from customer in the `Receive` and replace `messagetext`

- We are appending the incoming message from customer and looping the message to the bot node

- The loop continues until agent escalation is requested by the customer which is when the `onAgentAnswer` event the bot woud trigger 

- After this we queue the task and contact is delivered to agent

### 2. Update the FBM Inbound workflow 
- Login to Connect and open the working FBM Inbound workflow

- Add and configure the following nodes, `QnA Bot` , `Messenger` , `Append Conversation` , `Receive` , `Append Conversation`

- Connect the `Create Task` node to `QnA Bot` node 

- Open `QnA Bot` update the below values and Save
    
    - BOT: Select your bot in this dropdown
    
    - MESSAGE: $(messagetext)
    
    - PS ID: $(n2.messenger.psId)

- Connect the `QnA Bot` (onSucess event) to the new `Messenger` node

- Open `Messenger` node and update the below values and Save 
    
    - DESTINATION TYPE: PS Id
    
    - DESTINATION: $(n2.messenger.psId)
    
    - MESSAGING TYPE: RESPONSE 
    
    - NOTIFICATION TYPE: REGULAR
    
    - MESSAGE TYPE: TEXT
    
    - MESSAGE: $(n955.qnabot.text_response)
        
        - n955 is the node ID of the `QnA Bot` node used in the demo
        
        - This value might might be different in your configuration
        
        - Verify and Use the `QnA Bot` nodeID

- Connect the `Messenger` node to `Append Conversation`

- Open the `Append Conversation` node and update the below values and Save 
    
    - METHOD NAME: Append Chat 
    
    - NODE RUNTIME AUTHORIZATION: Create a new AUTH or add an existing AUTH 
    
    - CHANNEL: Facebook Messenger
    
    - CONVERSATION ID: $(ConversationId)
    
    - Direction: Outbound
    
    - TEXT: $(n955.qnabot.text_response)
        
        - n955 is the node ID of the `QnA Bot` node used in the demo
        
        - This value might might be different in your configuration
        
        - Verify and Use the `QnA Bot` nodeID
    
    - TIMESTAMP (IN UTC): $(n956.send.sentDateTime)
        
        - n956 is the node ID of the `Messenger` node used in the demo
        
        - This value might might be different in your configuration
        
         - Verify and Use the `Messenger` nodeID
    
    - ATTACHMENTS: $(parseDataAttachment)

- Open the `Receive` node and update the below values and Save 
    
    - Under `Configuration` tab
        
        - Select 'Receive Messenger message/event'
        
        - FROM (PSID): $(n2.messenger.psId)
        
        - EVENT NAME: Incoming Message
    
    - Under `Transition Actions` tab, configure action
        
        - TIME: On-Enter
        
        - ACTION: Set Variable 
        
        - VARIABLE: messagetext
        
        - VALUE: $(n959.receive.message)
            
            - n956 is the node ID of the `Receive` node used in the demo
            
            - This value might might be different in your configuration
            
            - Verify and Use the `Receive` nodeID

- Connect the `Receive` node to `Append Conversation`

- Open the `Append Conversation` node and update the below values and Save 
    
    - METHOD NAME: Append Chat 
    
    - NODE RUNTIME AUTHORIZATION: Create a new AUTH or add an existing AUTH 
    
    - CHANNEL: Facebook Messenger
    
    - CONVERSATION ID: $(ConversationId)
    
    - Direction: Inbound
    
    - TEXT: $(messagetext)
    
    - TIMESTAMP (IN UTC): $(n956.send.sentDateTime)
        
        - n956 is the node ID of the `Messenger` node used in the demo
        
        - This value might might be different in your configuration
        
        - Verify and Use the `Messenger` nodeID
    
    - ATTACHMENTS: $(parseDataAttachment)

- Connect (loop back) this `Append Conversation` node back to `QnA Bot` node

- From `QnA Bot` conenct the `AgentAnswered` event to the original `Messenger Node` in the FBM Inbound workflow

- In all the newly added nodes, make sure to configure the node outcomes appropriately, else there will be an error while publishing the flow

- Publish the flow

Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial page created | Gagarin JS (gasathiy@cisco.com) | 09 Nov 2021 |
| 2.0 | Video content upload | Gagarin JS (gasathiy@cisco.com) | 18 Nov 2021 |
| 1.0 | Text instructions created | Gagarin JS (gasathiy@cisco.com) | 18 Nov 2021 |


### Congratulations, you have completed **ALL section**. Well done!!!
### We would like to keep track of your progress and make sure that we are giving you effective support. Please take approximately one minute to complete a short survey.

<script>
function celeButton() 
	{
	window.open("https://app.smartsheet.com/b/form/ff1e015c4aed46bfab3f5caed7850aa4", '_blank');
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