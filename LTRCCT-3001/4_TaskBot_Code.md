---
title: 'Lab 4: Creating a Task Bot using Code'
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
  - [Planning the API Calls Using Code](#planning-the-api-calls-using-code)
  - [Before We Add Code](#before-we-add-code)
  - [Let's Add Some Code!](#lets-add-some-code)
  - [Testing Your Bot](#testing-your-bot)
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
- Intents - Triggers to which your bot will respond
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
   - Entities:
     - Email address (we already asked for this)
     - Order number (string)
   - Intent: 
     - Update Order
   - Utterances:
     - be creative 
   - Let's assume that an agent will need to work with the customer after we gather the Entities 

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
  > Add utterances 
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
  - Add some responses that will prompt the customer to enter in the connect information. (Example: Which Color? Or Which Item?)
- Open [Variable Documentation](https://help.imiconnect.io/docs/response-designer#list-of-common-response-variables) in a new tab.
- Locate the template which you created to respond to your intent
  - Populate the response with the Entities and Intents that you will be using as variables. (Example: ${entity.Color} ${intent})
- Locate the Greetings template
  - Update the response to include ${consumerData}
    - We will make some adjustments during the testing

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
  - Note the Greeting is giving you all of the consumerData
    - Find where the Name which you provided in the form is shown
    - Go into the Bot Builder and update the Greeting Response to say "Hello [name that you provide], how can I help you today?
    - Click update and then Make Live in the upper corner of the Bot Builder
    - In the website chat, send teh message Hello
      - Did you see your new response?
- Test your bot using your training phrases
  
  ---

## Preparing for the API calls
- Launch Postman
- Import the lookup for Widgets and Bobbles


  - ```curl --location --request GET 'https://629f77cc8b939d3dc2987fa4.mockapi.io/api/v1/Widget?color=red' ```
  - ```curl --location --request GET 'https://629f77cc8b939d3dc2987fa4.mockapi.io/api/v1/Bobble?color=red' ```


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


## Planning the API Calls Using Code
- Let's compare the API calls that we are making
  - What is the difference in the urls?
  - Can we create a pattern and inject the required changes to the url programmatically?
    - We can construct the url as a string using one of our entities in the path.
  - Do the responses need to be handled differently for the different items?
    - No.  When we compare both calls in Postman, we can see that we are returned the same JSON template. So we can use the same JSON path (which we got from JSON Path Finder) to tease out our data.
  

## Before We Add Code
  - Bot Builder uses a very specific version of Python
    - You cannot use dot notation for variables, but we can for imported modules
      - To set x as a variable of "newdfState.model_state.intent.name" it will look like this:
      -  ``` x = variables['newdfState']['model_state']['intent']['name'] ```


## Let's Add Some Code! 
- Find your Response template for Check stock
- Click to add a code snippet
- Put the code snippet above the text response
- We will start by importing requests and declaring our variables so that we can make our calls
  - remember to lookup the variable path in the [documentation](https://help.imiconnect.io/docs/response-designer#list-of-common-response-variables)


```
import requests

#variables
item = variables['newdfState']['']['']['']['value']
color = variables['newdfState']['']['']['']['value']

```
- Next let's construct the request
  - note that we are using a payload for a GET request???

```
url = 'from Postman' + which recently declared variable

payload = {'color': color}
headers = {}

response = requests.request('GET', url, headers=headers, params=payload)
```

-Now let's parse our response and store it where we can use it later

``` 
#Parsing out our data from our response
variables['dataStore']['stockCount'] = response.json()[x]['name from response payload']

#Passing the output back to the Bot Builder
output ={'dataStore': variables['dataStore']}
```

-Let's create our response in the Bot Builder
  - Just like we exposed variables in the [Creating Responses](#creating-responses) section, we are going to create a response string where we mix text and variables from the system.
  - We want the response to read something like "There are 48 Red Bobbles in stock.  Is there anything else that I can do for you?"

- After you have completed your code and response.  Click update in the upper right corner and then click make live.
 
## Testing Your Bot
- Click the preview button in the upper right corner and test out your intent with the training phrases that you setup
- Now test your bot from your website 

- Now complete the other [use cases](#use-cases) listed above.

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

