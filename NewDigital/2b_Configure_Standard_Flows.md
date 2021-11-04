---
title: 'Lab 2(b): Configuring Standard Flows'
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/d3ZIhE4UZDI" title="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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



Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Chandra Sekhar Gali | 27 Oct. 21 |


