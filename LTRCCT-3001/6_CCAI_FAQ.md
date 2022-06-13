---
title: 'Lab 6: Creating a FAQ in Dialogflow'
---

# Table of Contents
- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
  - [Enabeling FAQ in Dialogflow](#enabeling-faq-in-dialogflow)
  - [Importing FAQ](#importing-faq)
  - [Testing from within Dialogflow](#testing-from-within-dialogflow)
  - [Testing via Webex Connect chat](#testing-via-webex-connect-chat)
    - [Congratulations, you have completed this section!](#congratulations-you-have-completed-this-section)

# Introduction
In this lab we are going to import a FAQ in Google Dialogflow from an existing website, which will act similarly to the Q&A bot in Webex Connect.  We will then select some Questions and transform them into intents.

## Enabeling FAQ in Dialogflow
- In the Dialogflow portal:
- Click the Cog next to the name of your bot
- Under General Toggle "Enable beta features and API" and click save.


## Importing FAQ
- We are going to import our FAQ from the CDC's Covid-19 FAQ.
  - [CDC FAQ Website](https://www.cdc.gov/coronavirus/2019-ncov/faq.html)
  

- Click on the Knowledge (Beta) menu option
- Click Create Knowledgebase and name if Covid and click Save
- Next to "No knowledge document has been created yet" click create the first one.
    > Document Name: Covid FAQ
    >
    > Knowledge Type: FAQ
    >
    > Mime Type: text/html
    >
    > Data Source: URL: `https://www.cdc.gov/coronavirus/2019-ncov/faq.html`
    >
    > Enable Automatic Reload: True
    >
    > Click Create

    ---
- Now we need so allow Dialogflow to respond to out customers.
  - Click the Add Response button
    - You will see that a response string automatically populates that looks like `$Knowledge.Answer[1]`
    - Click Save at the top of the page
  --- 
  
## Testing from within Dialogflow
- In the upper right corner, you will see a try it now prompt
  - Using one of the questions from the FAQ, ask a question or a variation of the question.


## Testing via Webex Connect chat
- Launch your chat from your website
- Using one of the questions from the FAQ, ask a question or a variation of the question.






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