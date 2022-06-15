---
title: 'Lab 7: Improving your existing Dialogflow'
---

# Table of Contents
- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
  - [Converting Questions to Intents](#converting-questions-to-intents)
  - [Let's test our bot from inside Dialogflow](#lets-test-our-bot-from-inside-dialogflow)
  - [Testing using your website.](#testing-using-your-website)
  - [Adding Fulfillment](#adding-fulfillment)
    - [Congratulations, you have completed this section!](#congratulations-you-have-completed-this-section)

# Introduction
In this lab we are going to improve on our FAQ Dialogflow bot, by converting some of our FAQs into intents, requiring some entities, and taking an action on the information that we gather.


## Converting Questions to Intents
- Let's make a question become an intent so that we can move into the role of providing a service
- Go into Knowledge > find our FAQ > Click View Details
- Select `What are COVID-19 Community Levels?` and click convert it to intent. 
- Confirm conversion
- Click Save
- Click Intents and find your newly created intent.
  - Let's edit the response so that we can provide a link where the customer can lookup the current level for theit state and county.
    - Click in the response and add `You can view the current level by visiting https://www.cdc.gov/coronavirus/2019-ncov/your-health/covid-by-county.html.` at the end of the response
    - Click Save in the upper right corner.
    - Try it out in the "Try it out" section
- Let's move another FAQ into an intent, but this time we will ask additional questions and gather informaton using entities.
  - Convert `What should I do if I have been in close contact with someone who has COVID-19?` to an intent.
  - Find the newly created Intent and edit the response to include `Are you having symptoms?`
  - Click Save
  - Let's add an Entity to capture the answer to the question that we are asking
  
    > Click on Entities
    >        
    > Click Create Entity
    >
    > Name: Symptom
    >
    > Create the folowing: feaver, chills, trouble breathing
    cough
    > 
    > Add some synonyms like `elephant on my chest` for trouble breathing or `cold` for chills   
    >
    > Make sure that allow automated expansion is toggled on
    >
    >Click Save
     ---
  
  - Click Intents again and hover over the Intent that you just updated
  - Click the add a follow-up intent
    - Select the `Yes` intent
    - Open the new intent branch and scroll down to the response
    - Create a resoponse like `What symptoms are you having?`
    - Under Actions and Parameters 
      - Add the symptom Entity
      - Mark it as Required
      - Mark it as a List
      - Click Save
    - Go back to Intents and add an additional branch off from the `Yes` branch and select `custom`
      - Open the new Intent
      - In Actions and parameters
        - Remove any test in the text box and replace it with `LIVE_AGENT_HANDOVER`
        - Make your response `Sending you to an agent for additional assistance.`
        - Click Save
    - Go Back to Intents and add a new branch off from the `Knowledge.Covid.Covid FAQ.What should I do if` and select `No`
      - Open the new Intent
      - Add the response `Is there anything else that I can do for you?`
      - Click Save
  
## Let's test our bot from inside Dialogflow
  - In the "Try is now" section in the upper right corner
    - Enter the test phrase `What should I do if I have been in close contact with someone who has COVID-19?`
    - Enter `yes`
    - Enter `I have a cough and chills.`
    - Did you get the response that you expected?
      - If not, click on training and find where the planned flow deviated, in this case it would be `yes`.
      - Scroll down to where you see that you are giving symtoms and select the correct intent `Knowledge.Covid.Covid FAQ.What should I do if - yes - custom`.
      - Now test again.

## Testing using your website.
  - Go to your Glitch website and launch the chat
  - Run the same tests as above.

## Adding Fulfillment 
  - In Dialogflow, click on Fulfillment
    - Enable Webhook
    - Enter your `requestcatcher.com` url
    - Go to your `Knowledge.Covid.Covid FAQ.What should I do if  - yes - custom` intent and toggle `Enable webhook call for this intent`
    - Click Save
  





### Congratulations, you have completed this section! 

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/CCAI.html";}
function nextLab() 
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-3001/6_CCAI_FAQ.html";
 }
</script>

<div id="button-row">
<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go To Previous Lab</button>

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go to the Next Lab</button>

</div>