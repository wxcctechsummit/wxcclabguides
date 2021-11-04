
# Lab 1(a): Control Hub and Portal Changes

Video example

<iframe width="560" height="315" src="https://tscfeedbacklive.azureedge.net/uploads/g013900fVZj3IKipdytZVHX34abbH/feb846bb-5c8a-4395-b60a-4a403ee3d514.mp4?sv=2019-07-07&sr=b&sig=CRFbEJ8bvCZJyUahUHub2zlKSX9qNADunxkRKgKe34k%3D&st=2021-10-21T07%3A55%3A31Z&se=2021-10-22T08%3A00%3A31Z&sp=r" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents
1. Control Hub Digital channels verfication
2. New component cross-launch

# Introduction

## Lab Objective

This lab is designed to verify that the new digital channels is enabled in the tenat you are working and you are able to access the new components successfuly.   

## Pre-requisite

1. Admin credentials to login to Control Hub and WxCC administration portal.

# 1. Control Hub Digital channels verfication

- Go to https://admin.webex.com
- Login with tenant administrator credentials 
- Under 'Services' select  'Contact Center' > 'Settings' > 'General'
    - Verify under 'Service Details' > 'Digital Channel' is set to 'IMI Digital'
- Under 'Services' select  'Contact Center' > 'Settings' > 'Digital'
    - Verify Digital channels setup for Webex Contact Center is completed.

![Banner](imi_images/CH_settings.jpg)

![Banner](imi_images/CH_settings_2.jpg)

# 2. New component cross-launch
- 'Services' select  'Contact Center' > 'Settings' > 'General' > 'Advanced Configuration' > Select 'Go to Webex Contact Center Management Portal' to cross launch to administration portal 
- In Administration portal, select 'New Digital Channels' to cross launch into the new component 'Engage' 
    - No additional login(or credentials) are required. The login to Engage portal should be seamless
- In Engage portal, select Users > Search 
- Verify that users with Administrator and Premium Agent previleges are replicated with role type 'Administrative' and 'Customer Care' roles
- Please note that the user account with which you have logged in will not show up in the engage user list. This is expected behaviour. 

![Banner](imi_images/CH_settings_3.jpg)
![Banner](imi_images/Portal_1.jpg)
![Banner](imi_images/Engage_1.jpg)

Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Gagarin JS (gasathiy@cisco.com) | 31 Oct 2021 |



