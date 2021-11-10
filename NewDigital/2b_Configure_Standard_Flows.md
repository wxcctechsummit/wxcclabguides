---
title: 'Lab 2(b): Configuring Standard Flows'
---

`Please review this video before you proceed with this lab task.` 

<iframe width="1024" height="576" src="https://www.youtube.com/embed/jt-cLg_8Axc" title="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

`Lab task video`
<iframe width="1024" height="576" src="https://www.youtube.com/embed/d3ZIhE4UZDI" title="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents

1. Upload and Configure the Standard Flows
2. Add Authorization to Cisco and Engage Nodes


# Introduction

## Lab Objective

This lab is designed to ensure we will be able to upload and configure the Standard Flows and add authorization to Cisco and Engage Nodes and publish the workflow.  


## Pre-requisite

1. Admin credentials to login to IMI Connect
2. Admin credentials to WxCC administration portal
2. Engage Client ID, Client Secret, Domain (Customer/Partner Admin receives these details from CSAM when tenant is provisioned)



# 1. Upload and Configure the Standard Flows

- Access IMI connect URL (this is specific to the tenant you are using) 
- Login with tenant owner or administrator credentials
- Go to Services -> Create New Service -> Enter Service Name -> Save
- Go to Flows -> Create New Flow
- Enter Flow Name -> Select Type as "Workflow"
- Select Method as ‘Upload a Flow’
- Upload the Flow
- Choose respective Task and Save


# 2. Add Authorization to Engage Nodes

- Click on Enage Node
- Go to Node Runtime Authorization -> Add New Authorization
- Enter Authorization Name
- Add the details recieved from CSAM
- Click Authorize 
- Select the created Authorization and Save


# 3. Add Authorization to Cisco Nodes

- Click on Cisco Node
- Enter WxCC Admin creds and Authorize
- Authorization Success message will be seen
- Select the created Authorization and Save
- Once all the Cisco and Enagage Nodes are updated with Authorizations -> Click Make Live

---

### Congratulations, you have completed this section! 
### We would like to keep track of your progress and make sure that we are giving you effective support. Please take approximately one minute to complete a short survey.

[Back to top](#table-of-contents)

---

Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Chandra Sekhar Gali (chgali@cisco.com) | 27 Oct 21 |
| 2.0 | Format Changes | Gagarin JS (gasathiy@cisco.com) | 09 Nov 2021 |
| 3.0 | Adding pre-configured template info | Gagarin JS (gasathiy@cisco.com) | 10 Nov 2021 |

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/NewDigital/HomePage.html";}
function nextLab() 
 {
 window.open("https://app.smartsheet.com/b/form/ff1e015c4aed46bfab3f5caed7850aa4", '_blank');
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/NewDigital/2c_Flow_debugging.html";
 }
</script>

<div id="button-row">
	<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Go back to Main Page</button>

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Take Survey and Go to Next Lab</button>


</div>
