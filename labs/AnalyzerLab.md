---
title: "Lab 8: Reporting & Data"
---

# Webex Contact Center Reporting - Analyzer

# Table of Contents

- [1. Login into Analyzer and review user interface](#1-login-into-analyzer-and-review-user-interface)
- [2. Execute Stock Report and use it to create custom reports](#2-execute-stock-report-and-use-it-to-create-custom-reports)
- [3. Create an Agent Historical Call Visualization](#3-create-an-agent-historical-call-visualization)
- [4. Create a Call Realtime Report](#4-create-a-call-realtime-report)
- [5. Create Dashboard](#5-create-dashboard)

**Quick Links**

* [Portal](https://portal.wxcc-us1.cisco.com/portal)
* [Analyzer](https://analyzer.wxcc-us1.cisco.com/analyzer/home)

# Introduction
<iframe width="560" height="315" src="https://www.youtube.com/embed/453BlLMFetU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> 

## Lab Objective

This lab is designed to give you basic understanding of Analyzer, user interface features , how execute stock reports and use them to create custom reports per your need.  

We will also be creating two new reports (one for Call and one for agent) to capture relevent information and then will use these reports in a dashboard, while doing this we will learns about capabilities and features you can use to capture the required insights.

## Pre-requisite

1. All previous labs completed
2. Admin or supervisor credential with Analytics access in user profile
3. Make sure to make few test calls and answered by the agent the day you attempting this lab (to ensure we have some data to analyze)


# 1. Login into Analyzer and review user interface

<iframe width="560" height="315" src="https://www.youtube.com/embed/E4Ch2gUSRi4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> 


**Section Information**
- Login Into Analyzer 
- Four Repositories
- Review Stock reports and Dashboard
- Search Folder & Visualization
- List or Grid View
- Visualization Summary information
- Report Details information

1. Click on the `Burger` sign next to `HOME`
2. You can see 3 modules on the left pane : `Visualization , Dashboard and Variables`
3. In the middle of the page you would notice 4 Repositories : `Total Agent Activity Records, Total Agent Session Records, Total Customer Activity Records and Total Customer Session Records`
4. Click on More details on Total Customer Session Records: Make a note of `total` customer sessions records and `period`  those records were executed
5. Click on `Visualization`: you will notice `Stock Reports` Folder , Click on `Stock reports --> Business Metrics`
6. Click on `GRID` option on left upper side (under the user name), this will show you reports in GRID view 
    Make a note of `Type, Temporal Scope, Last Modified , Created By and ID`
7. Click on Search `Folder & Visualization` and enter `Agent realtime`
    This is execute a global search and list the matching report



# 2. Execute Stock Report and use it to create custom reports

<iframe width="560" height="315" src="https://www.youtube.com/embed/29K4JbR8Tps" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> 

**Section Information**
- Create a folder
- Save a stock report as custom in your folder
- Execute Your report
- Information in preview
- Run a Stock Dashboard

1. Go to `Home --> Visualization`
2. Click on `Create New`  and select `Folder` to create a new folder with your name
3. Click on ` Stock Reports -> Historical -> Reports -> Agent Reports`
4. Take cursor on top of `Agent Details` report, click 3 dots and click `Create a Copy`
5. Click `Save As..` , select the Folder you created previously, change the Report name to something custom to your self (For example KT_Agent Details) and click `OK`
6. Not close this report by clicking x on right upper side.
7. Go back to your Folder under `Home ->  Visualization` and Double click (or click on 3 dots and click `Run`) on your newly added report to run it.
9. Now you are in Preview mode and to check the `data summary` for this report  click on burger sign next to `setting` on the header. Make a note of `Data Summary` and `Details`
10. Click on `Export` option and download this report in `Excel` or `CSV` format.
11. Make a note of informational `Timezone` information on right hand upper side and make sure this match with your browser time.
12. Click on `Dashboard -> Stock Reports -> Historical Reports -> Contact Center Overview`
13. Double click `Contact Center Overview - Historical` . This will should your Contact Center Historical Summary

# 3. Create an Agent Historical Call Visualization 

<iframe width="560" height="315" src="https://www.youtube.com/embed/xKoAPtAtXzo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>  

**Section Information**
- Create a Historical Agent report
- Repository and Interval Selection
- Using Measures and Profile Variables
- How to use Enhanced Field
- How to creat new Formulas


1. Go to `Home --> Visualization` and Click on your `Folder` created in previous excercise.
2. Click on `Create New` --> `Visualization`
3. On the top pane Click next to `Type` and select `Agent Session Record`
4. On left pane click next to `Start Time` and select `Last 7 Days`
5. Click on `Compute` and select under `Interval` Daily
6. Click on `+ Row Segment`, search for Field `Agent`. Select `Agent Name` and drag it to `Row segment` area (Green color pane)
7. Click on `Interval` on `Column Segment` and drag it to `Row Segment` under `Agent Name`
8. Click on `+ Profile Variable` , search for `connected` and click on `Measure` drop-down. Select `Connected Count` and drag it to `Profile Variable` pane (Green). Here click on `Formula`  and select `Sum of Connected Count`, change the name to `Inbound Calls` and Click `Save`
9. Repeat `step 7` and drag `Outdial Connected Count` and Save `Sum of Outdial Connected Count` as `Outdial Calls`
10. Click `Save` option on the top pane
11. Name the report as `Agent Call Volume Last7Days`  and click `OK`
12. Click on `Preview`, You can see `Calls handled (Inbound and Outbound)` by all the agents for `last 7 days.`
13. Lets see how can we leverage `Enhanced Field` to create Grouping of `Segment fields`.
14. Go to `Edit view` of the report, right click on the `Agent Name` and click on `Create Enhanced Field`
15. Change the `Name` to `LOB_{YourNameInitial}`, Type `Default` in `Default Group` 
16. In `Group` configure `Group Name` as `Sales` and select your `agent` in `Provide Value`  and `Save` it
17. Now move the newly created `Enhanced field` above `Agent Name` by click and drag in the segment section.
18. Now this `Enhanced field` can be saved to use globally in other reports by `right click` on the field and click `SAVE`  and `SAVE`.
18. `Save` the report and `Preview`: You will see `Enhanced Field` in first column : `Default` and `Sales` with your agent assigned under `Sales` and rest of the agents under `Default`.
19. Lets see how we can create `Custom formula`: In this case we would like to get a field which give us `total number of calls handled by the agent including inbound and outbound`.
20. Go to the `report edit view` and right Click on `Inbound Call`--> `click New Formula`
21. Name the formula as `Total Agent Call_{YourNameInitial}`
22. In Arithmetic Expression Use `Inbound Call + Outdial Calls` (Click the down arrow to see the field) and `Save`
23. This Formula can be saved for global use in other reports, to do so `right click` on the newly created formula variable and click `save` and then `OK`
23. `Save` the report and `Preview`, this will add new column providing you `Total number of calls`


 

# 4. Create a Call Realtime Report

**Section Information**
- Creating a Realtime Report 
- How to use Filter
- Use Drill-down functionality

<iframe width="560" height="315" src="https://www.youtube.com/embed/zQUnVZxMETw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> 

1. Go to `Home --> Visualization` and Click on your `Folder` created in previous excercise.
2. Click on `Create New` --> `Visualization`
3. On the top pane Click next to `Type` and make sure `Customer Session Record` is selected
4. On Left pane click next to `Start Time` and select `Realtime`
5. Click on `Compute` and select `Start of Day`
6. Click on `Refresh Rate` and change it to `15` (Minutes) from default `5`
7. click on `+ Profile Variables` , search for `Session` and select `Contact Session ID`, drag it to `Profile Variable` pane.
8. Click on `Formula` select Value of `Contact session ID`
9. Repeat `step 7` to add these variables: `EntryPoint, Final Queue Name, Team Name, Agent Name`
10. Click `Save` option on the top pane
11. Name the report as `Call Session Today`  and click `OK`
12. Click on `Preview`, You can see Calls received Today (for all the entry points and calls answered by all the agents)
13. Now to see the calls today answered by you  only lets `add a filter `in this report
14. Go To the `Report edit view` and on left pane click on `Add Filter`
15. Here search for `Agent` and select `Agent Name` and drag it to `Filter area`
16. Now `Click under the Field,` as you do that analyzer will list possible values. Select your `Agent`  and Click `Save`
17. Now `Save` the report on top and `Click Preview`. Now you will only see calls handled by your agent.
18. Lets check on `Drill-down` Functionality now. 
19. In your Preview report click on any one of `Contact Session ID Value` (alpha numeric string), as you click you will see a `Zoom icon`. Click it.
20. This will open a new Window with `Drill-Down view`, essentially showing you all the Activities during this session (start with Activity state - new)
21. In this Drill-Down window on left pane click on `Agent name`, Moment you click it this data will be added to the Drill-down and show you value for each Activity in this session, more fields can be added like this.
25. Click on `Launch` icon to open this Drill-down window in a separate window with `full view`.



# 5. Create Dashboard

<iframe width="560" height="315" src="https://www.youtube.com/embed/JV5zVsI-3vo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> 

**Section Information**
- How to create Dashboard

1. Go to `Home -->  Dashboard`
2. Click on your `Folder`
3. Click on `Create New --> Dashboard`
4. On left pane you would see your `Folder` , click it. Here you will see two reports you created in previous excercise
5. Drag these one by one into the `Dashboard pane`. Now by clicking on right bottom corner of these reports you can maximize them as per your preference 
6. Click `Save` and set the name `Dashboard_{Name Initials}`
7. Click `Preview` to see your Dashboard (With one Historical and one Realtime Report)


Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Krishna Tyagi (ktyagi) | 25 Jan 2021 |
| 1.1 | Final Release | Mike Turnbow (miturnbo) | 27 Jan 2021 |

