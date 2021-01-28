
## Part 1 : 

**Video Provisioning, Login, ACD Config and Data Server Configuration**

<iframe width="560" height="315" src="https://www.youtube.com/embed/3PMElHzkpfE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


# Introduction

## Lab Objective

This lab is designed to educate partners on provisiniong requests, ACD and Data Server Configuration (Performed by WFO Team), login, user administration, roles, views, smart desktop, retention rules and workflow administration.
**This lab is intended to be a demo only**

## Pre-requisites

1. Webex Contact Center Portal URL.
2. WFO enabled in Webex Contact Center Tenant
2. Admin credentials for configuration (Both Webex Contact Center and WFO - Calabrio)

### 1. WFO Tenant Provisioning request

- Normally performed by WFO Team, this is intended to be a video demo only


### 2. Login Steps

- URL - https://portal.wxcc-us1.cisco.com/portal/home.html
- Customer admin, expands left navigation menu and click on WFO Optimization Module.
- New tab launches, login using your WFO admin credentials. 

### 3. ACD Configuration

- Normally performed by WFO Team, this is intended to be a video demo only



### 4. Data Server Configuration

- Normally performed by WFO Team, this is intended to be a video demo only

## Part 2
**Video User Management**
<iframe width="560" height="315" src="https://www.youtube.com/embed/ar-pjwt1hho" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 5. User adminitration

- Click on Application Management Module.
- Under User configuration, click users.
- "What Do You Want To Do?", edit an existing user and select a user from the drop down menu.
- Fill in username (email address), windows login is required for screen recording, if not needed you may leave it blank.
- Set a password.
- Confirm roles is setup to agent (if user is an agent.  If supervisor, role should be set to Supervisor.
- Confirm team (WFO Teams are not tied to Contact Center teams, they are independant of each other.)  Based on customer requires select the appropriate team.
- Associated Groups and Teams - Leave none selected (This will only grant access to agent's records).
- WFM Views - Select one view per customer requirements.  If multiple views, and one view must be designated as the Main View.
- QM Views - For QM, the user can be assigned one or more views. Users will have scope over contacts that are filtered by that view. If you apply a view to a user, it supercedes any organizational scoping.
- Display Time Zone - It should be set to the user's local time. It defaults to the organization's time zone configured under Global Settings
- Scheduling - Place a check mark on "Enable scheduling for this user"
- Scheduling Time Zone -  It defaults to the organization's time zone (configured on the Global Settings page), but it can be changed for agents who should be scheduled in another time zone.
- Seniority - Optional
- Main Service Queue - Select the agent's primary service queue.
- Skill Mappings - Assigned the service queues the agent can be scheduled for.
- Standard Work Shift Rotation - Assign one or more work shifts to the agent based on customer requirements.
- Copy Work Shift Rotations - Optional
- Vacation Hours - Optional
- Schedule Release Profile - Optional


## Part 3
**Video Roles, Views, and Smart Desktop**
<iframe width="560" height="315" src="https://www.youtube.com/embed/-BvtpdgFyq8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 6. Roles - 
- Create new role and define license types and permissions.

### 7. Views - Create new and/or modify views based on customer requirements.
- Create new and/or modify views based on customer requirements.

### 8. Smart Desktop, Retention, Workflow administration
- Application Management -> Administration -> Click downloads -> Select Calabrio One Smart Desktop or SCCM_Support.msi (depending on customer requirements).
- Create a new retention policy -> All fields should be set to 75 days.
- Create a Workflow Administration -> Create a new flow, End of call event, "Sales Outbound", save it.  Locate newly created rule and click on it.  Add conditions per your requirements.


### 9. Thank you, we want your feedback.
- Please submit your feedback

Changelog:

| **Version** | **Comments**      | **Author(s)**                    | **Date**    |
| ----------- | ----------------- | -------------------------------- | ----------- |
| 1.0         | Initial Release   | Mike Turnbow (miturnbo) | 28 Jan 2021 |
| 2.0         | Final Release   | Mike Turnbow (miturnbo) | 28 Jan 2021 |
