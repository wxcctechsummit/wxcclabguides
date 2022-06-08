---
title: 'Lab 4: Creating a Task Bot using Flow Builder'
---

# Table of Contents
- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
  - [Tools we will be using](#tools-we-will-be-using)
  - [Vocabulary](#vocabulary)
  - [Use Cases](#use-cases)
  - [Training](#training)
      - [Creating Entities](#creating-entities)
      - [Creating an Intent](#creating-an-intent)
  - [Creating Responses](#creating-responses)
  - [Testing Initial Bot Logic](#testing-initial-bot-logic)
  - [Testing Your Bot via Live Chat](#testing-your-bot-via-live-chat)
  - [Preparing for the API calls](#preparing-for-the-api-calls)
  - [Launch Flow Builder](#launch-flow-builder)
    - [Congratulations, you have completed Lab 4 tasks!](#congratulations-you-have-completed-lab-4-tasks)
 
    - [Congratulations, you have completed Lab 4 tasks!](#congratulations-you-have-completed-lab-4-tasks)

# Introduction
In this portion of the lab, we will be configuring the bot itself.  We have three different use cases that we are going to complete so that we can take some of the load off of our customer service team.  We will be collecting information, deciding if we need to handoff to an agent, making API calls, and relaying information back to the user.

## Tools we will be using
- Postman
- Bot Builder
- requestcatcher.com
- jsonpathfinder.com
- mockapi.io
- Webex Connect Flow Builder

## Vocabulary 
- Intents - Triggers that you bot will respond to
- Utterances - Training phrases that will map to Intents
- Entities - A kin to variables for running tasks. 
- Slots - Entities that are used in Intents.
- Responses - Follow up to either get additional information regarding an entity or a response to an intent. 

## Use Cases
1. Check if an item is in stock
   - Entities:
     - Stock Item: Custom list: Widget, Bobble
     - Color: Custom List: Green, Red, Yellow, Blue, Purple, Silver, Orange
    - Intent:
      - Check Stock
    - Utterances:
      - Do you have green bobbles?
      - Do you have red widgets?
2. Change my order
3. Check shipping status 


## Training
- Click Training <img src="images\Lab4_Training_menu.PNG" height="25">
#### Creating Entities 
- Select Entities
- For Each Entity:
  - Click Create Entity
    > Name: name of entity (don't use spaces)
    >
    > Entity Type: pick data type
    >
    > If using a Custom List:
    >
    >> Populate the list with values.
    >> 
    >> Add any Synonyms that are necessary
    
    ---

#### Creating an Intent
- Select Intents
- Click Create Intent
  > Name your intent (Example: Check Stock)
  >
  > Add uterances 
  >
  >> Create a phrase similar to what a user might enter.
  >>
    >>  In the Slots section:
    >>
    >>> Click link entity 
    >>>
    >>> Select any entities that you will use for this intent
    >>>
    >>> Click the **Required** checkbox if they are required
    >>>
    >>> Select or create a new **Template Key** (Will be used to prompt for missing information)
    >>
    >
    > Click on words which represent **Entities** 
    >
    > <img src="images\Lab4_Map_Entity.gif">
    >   
    >In the **Response** Section Click on final template key
    >> Select or create a Template key which will be used to respond to the intent once required slots are filled. (Example: Lookup Item)
    >
- Toggle reset slots after completion to True
- Click Save.
- Click Train and supply a reason for training.

    ---

## Creating Responses
-  Click Responses <img src="images\Lab4_Responses_menu.PNG" height="25"> 
- Locate the templates which you created for entity slot filling 
  - Add some responses that will prompt the customer to enter in the connect information. (Example: Which Color?)
- Open [Variable Documentation](https://help.imiconnect.io/docs/response-designer#list-of-common-response-variables) in a new tab.
- Locate the template which you created to respond to your intent
  - Populate the response with the Entities and Intents that you will be using as variables. (Example: ${entity.Color} ${intent})
- Click Update
- Click Make Live

  ---

## Testing Initial Bot Logic
- Click back to the training section
- Click Preview
- Test your bot by using training phrases.
    
  ---

## Testing Your Bot via Live Chat
- Go to your website and launch a new chat
- Fill in the form values
- Test your bot using your training phrases
  
  ---


## Preparing for the API calls
- Launch Postman
- Import the lookup for Widgets and Bobbles
  - curl --location --request GET 'https://629f77cc8b939d3dc2987fa4.mockapi.io/api/v1/Widget?color=red'
  - curl --location --request GET 'https://629f77cc8b939d3dc2987fa4.mockapi.io/api/v1/Bobble?color=red'
- For each cURL:
  > File > Import > Raw test
  >
  > Paste the cURL command into the text area
  >
  > Click Continue
  >
  > Click Import
  > 
  > Click Send in Postman
  >
  > Open a new browser tab to [JSON Path Finder](https://jsonpathfinder.com)
  >
  > Copy the entire JSON payload from Postman 
  >
  > Paste the payload into the left pane of JSON Path Finder
  > 
  > Click the stockcount node on the right side of the screen and copy the path
  >
  > Replace the leading x with $

- Open a new browser tab to [Request Catcher](https://requestcatcher.com)
  - Use your Cisco Live lab ID as your subdomain
  - Click Get started
 
## Launch Flow Builder 
  
  - Create a copy of your Task Bot flow 
  - Go into your service > My flows > Create Flow
    > Name: your choice 
    >
    > Type: Work Flow
    >
    > Method: Copy From Existing Flow
    >
    > Select Flow: Your working bot flow
    >
    > Click Create
    >
    > Click Save


    ---

- Find the Task bot node and **delete** the **onSuccess** connector
- Add a Branch node above the Task bot node
- Connect the **onSuccess** node edge from Task bot to Branch 
- Open the Branch node
  > Rename Branch1: checkStock
  >  
  > Variable: Task Bot > taskbot.intent
  >
  > Condition: Equals
  >
  > Value: intent valuee (Check stock)
  >
  > Click Save
  
  ---

- Add an HTTP Rquest node above Live Chat or In-App Messaging node
- Drag the Green node edge connector from Branch to Http request node and select checkStock
- Drag another Green node edge connector from Branch to Live Chat or In-App Messaging node (it will auto select **None of the above**)
- Drag the rest of the Red and Orange node edge connectors to the Close Conversation node
- Drag the Green node edge from HTTP Request node to the
- Open the HTTP Request Node:
  > Method: Post
  >
  > Endpoint URL: https://CLLabID.requestcatcher.com
  >
  > Body: Task Bot > taskbot.entities
  >
  > Click Save
  >

   ---

- Click Save at the top of the flow
- Click Make Live
- Select your Application and click Make Live again
- While you flow is publishing
  - Turn off your old flow
  
  ---

- Once your new flow is published and the old flow is turned off
  - Create a new chat from your website and test your bot using your training phrases
  - Open the Request Catcher browser tab
  - Copy the last line into a notepad
- Go back into your flow
  - Click Edit in the upper corner
  - Drag a new Data Parser node into the flow above Append Conversation
  - Delete the **onSuccess** node connector from HTTP Request and attach it to the new Data Parser node
  - Open the Data Parser node
    > Input: Task Bot > taskbot.entities
    >
    > Sample Body: the data that you coppied from Request Catcher
    >
    > Click Parse
    >
    > Select the $.Color.name and $.stockItem.value
    > 
    > Click Import
    >
    > Create Output variable names (like color and item)
    >
    > Make both Variables Manditory
    >
    > Click Save
    >

    ---

  - Drag a new Branch node into the flow above Append Conversation
  - Connect the Green node edge from Dataparser to the new Branch node  
  - Connect all of the Red and Orange nodes edges to Close Conversation
  - Open the Branch node
    > Rename Branch1 to Widget
    >
    > Variable: Data Parser > item
    >
    > Condition: Equals
    >
    > Value: Widget
    >
    > Add branch
    >
    > Rename Branch2 to Bobble
    >
    > Variable: Data Parser > item
    >
    > Condition: Equals
    >
    > Value: Bobble
    >
    > Click save
    >
      ---

  - Drag 2 HTTP Request nodes into the flowabove append conversaton 
  - Connect the Green node edge from Branch to the first HTTP node and select Widget
  - Open the HTTP Request
  - Click on Transacton Actions
    > Click Add Action
    >
    > Time: On-Enter
    >
    > Action: Set Variable
    >
    > Variable:
      >>
      >> Add an new variable
      >>
      >> Variable name: stockURL
      >>
      >> Click Save
    >
    > Value: the url with the param left empty and then Data Parser > color (Example: https://629f77cc8b939d3dc2987fa4.mockapi.io/api/v1/Widget?color=$(n2316.color))
    >

  - Click Configuration
    > Method: GET
    >
    > Endpoint URL: Custom Variables > stockURL
    >
    > Connection Timeout: 1000
    >
    > Request Timeout: 1000
    >
    > Ouput Variable Name: itemCount
    >
    > Response Entity: Body 
    >
    > Response Path: $[0].stockcount (from Postman and JSON Path Finder/Import from Sample)
    >
  - Click Transaction Actions
    > Add action
    >
    > Time: on-leave
    >
    > Action: Set variable
    >
    > Variable: messagetext
    >
    > Value: There is (output variables > itemCount) (Data Parser > color) (Data Parser > item)s in stock. Is there anything else I can do for you?  
    >
  
  ---

- Connect the Green node edge from Branch to the first HTTP node and select Bobble
  - Open the HTTP Request
  - Click on Transacton Actions
    > Click Add Action
    >
    > Time: On-Enter
    >
    > Action: Set Variable
    >
    > Variable: stockURL
    >
    > Value: the url with the param left empty and then Data Parser > color (Example: https://629f77cc8b939d3dc2987fa4.mockapi.io/api/v1/Bobble?color=$(n2316.color))

  - Click Configuration
    > Method: GET
    >
    > Endpoint URL: Custom Variables > stockURL
    >
    > Connection Timeout: 1000
    >
    > Request Timeout: 1000
    >
    > Ouput Variable Name: itemCount
    >
    > Response Entity: Body 
    >
    > Response Path: $[0].stockcount (from Postman and JSON Path Finder/Import from Sample)
    >

  - Click Transaction Actions
    > Add action
    >
    > Time: on-leave
    >
    > Action: Set variable
    >
    > Variable: messagetext
    >
    > Value: There is (output variables > itemCount) (Data Parser > color) (Data Parser > item)s in stock. Is there anything else I can do for you?  
    >
    >

    ---




### Congratulations, you have completed Lab 4 tasks! 

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/4_TaskBot.html";}
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