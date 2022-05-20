---
title: 'Lab 7: Advanced Email Configuration'
---

# Table of Contents
- [Step 1. Email Workflow Overview](#step-1-gmail-account-configuration)
- [Step 2. Position In Queue Configuration](#step-1-gmail-account-configuration)
- [Step 3. Autoreply Configuration](#step-1-gmail-account-configuration)
- [Step 4. Improving Routing based on the Subject](#step-2-create-email-asset-and-register-to-webexcc)
- [Step 5. Screenpop configuration](#step-3-email-entry-point-and-queue-creation)
- [Step 6. Integration with Smartsheet using smartsheet APIs](#step-4-createupload-email-flow)


# Introduction

### Lab Objective

This lab will give you a detailed understanding of the predefined workflow logic. With that, you will be able to improve the script and do a more advanced configuration.
This lab includes multiple script customizations and shows how to create an HTTP Request which is needed for integration with external HTTP services (as an example it uses smartsheet API).


### Pre-requisite

- You have successfully compleated the the Lab1 and Lab2 (Email Configuration).

# Lab Section

## Step 1. Email Workflow Overview

>**Note**: For this lab, we created a Gmail account. Optionally, use your own account for polling and handling the emails. It can be a Gmail account or Office 365 account or any account which has email forwarding.

### 1. Google Account Setting – Enable POP3/IMAP setting


| **User email**                       |
| ------------------------------------ | 
| cl1webex**\<ID\>**@gmail.com   | 

> **Note:** Your \<ID\> was provided to you personally.  \<ID\> is the unique number equal to your POD.


- Login to the Gmail account with the credentials above[https://mail.google.com](https://mail.google.com){:target="_blank"}. The password is the same as for Webex admin account.

- Enable POP3/IMAP setting by clicking on settings icon on top right corner and selecting **See all settings**.

<img align="middle" src="images/Lab2_Gmail1.png" width="1000" />

- Now Click on **Forwarding and POP/IMAP**, enable the `POP Download` and `IMAP access` then click **Save Changes**.

<img align="middle" src="images/Lab2_Gmail2.png" width="1000" />




[Back to top](#table-of-contents)
---

### Congratulations, you have completed this section! 

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2013/Home.html";}
function nextLab() 
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2013/Lab8_AgentProductivity.html";
 }
</script>

<div id="button-row">
<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Main Page</button>

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Next Lab</button>

</div>
