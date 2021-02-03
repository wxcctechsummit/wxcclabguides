# Webex Contact Center APIs

# Table of Contents

## Part 1: Legacy 1.0 APIs - CSR, CSR Query

1. Pre-requisites - Ensure the API key is created for your user (Already done for you)
2. Pre-requisites - Create an Analyzer CSR Report
3. Pre-requisites - Check if call recordings are available
4. Make a few test calls to create data for the contact center
5. Fetch a single CSR (Contact Session Record)
6. Fetch CSRs for today or this this week using a query

## Part 1: Legacy 1.0 APIs - CARs and activity chains

1. Pulling a single CAR - Contact activity record
2. Retrieving Contact Activities for a call using event/activity chain information

## Part 3: New Contact Center APIs on Developer Portal - Tasks and Recordings

1. Introduction to the developer portal and exploring the endpoints available.
2. Retrieving the list of tasks (Contact Sessions).
3. Retrieving the list of call recordings for a specific set of task(s).
4. Download the recordings

# Introduction

## Lab Objective

- This lab is designed to ensure you are able to use retrieve reporting data using the Legacy APIs which are carried over from version 1.0 and into the New Webex Contact Center platform.

- The New Webex Contact Center APIs are currently in an Early release and have 4 endpoints available - GET Tasks, GET Agent Statistics, GET Queue Statistics and POST Capture Query (Call recording retrieval).

- We will explore both the flavors - authenticating using an API Key using the legacy API and using a Bearer token with the new Webex Contact Center APIs on the developer portal.

## Pre-requisite

Before you begin this lab:

1. You already have test calls made.
2. You understand how to create Analyzer reports. Review the analyzer lab if you need more information.
3. Call Recordings are visible under recording management.
4. You already have an API key generated for `admin1podX` where X is your pod number. View the video below to verify this. Reach out to the lab proctors if you require any information around this.
5. You have the Postman client downloaded and installed to make queries to the Webex Contact Center APIs. Downlod it here: [Download and Install Postman](https://www.postman.com)

**Important Links**

> Control hub - For your Org Id: https://admin.webex.com

> Portal: https://portal.wxcc-us1.cisco.com/portal

> Analyzer: https://analyzer.wxcc-us1.cisco.com/analyzer/home

> Legacy V1.0 endpoint - Resource: https://rest.wxcc-us1.cisco.com/aws/api/{record-type}/{id}

> Legacy V1.0 endpoint - Query: https://rest.wxcc-us1.cisco.com/aws/api/{record-type}?q={your-query}

### Part 1 - Legacy 1.0 APIs - CSR, CSR Query

>The following video outlines the pre-requisites as well as Part 1

<iframe width="560" height="315" src="https://www.youtube.com/embed/S0OO6rxciqo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Quick Links**

> Control hub - For your Org Id: https://admin.webex.com

> Portal: https://portal.wxcc-us1.cisco.com/portal

> Analyzer: https://analyzer.wxcc-us1.cisco.com/analyzer/home

> Legacy V1.0 endpoint - Resource: https://rest.wxcc-us1.cisco.com/aws/api/{record-type}/{id}

> Legacy V1.0 endpoint - Query: https://rest.wxcc-us1.cisco.com/aws/api/{record-type}?q={your-query}

> New Webex Contact Center API endpoint: https://webexapis.com/v1/contactCenter/{endpoint}


### 1. Verify that you have a Analyzer Report created and a Call recording exists
- Follow the steps outlined above to create an analyzer report by logging into Analyzer and creating a CSR report. It is assumed you already have completed the Analyzer Lab in the previous sections.

### 2. Verify you have Postman Installed
- Install Postman from the link.
- Create a Folder to store your requests.
- Create variables to hold critical information in all the requests. From Header and the Authorization Header.

### 3. Create a GET CSR Request.
- Review the CSRs in your setup using Analyzer.
- Draft the GET CSR request using the format

**Authorization API Key**:
To generate the HMAC (used in the Header of the API call), 
you will need to encode your user ID with the API key, using the HMAC SHA1 algorithm. 

You can use any HMAC generator online to convert the API Key into an HMAC Authorization Token that can be used in the header of the HTTPS request - for any operations against the API.
   (E.g: https://www.liavaag.org/English/SHA-Generator/HMAC/)

Input:

From (UserID) : `userID@portal-controlhub.com`

TEXT

Key:

API Key: `myRandomApiKeY`

TEXT

Encoding: SHA1

Output: Base64

Headers after HMAC encoding: 

    Authorization: `EnCoDeDaPiKeY=`
        
    From: `userID@portal-controlhub.com`

### 4. Plug these into Postman as described in the video.
- Run the GET CSR request using: 

`https://rest.wxcc-us1.cisco.com/aws/api/csrs/{your-example-contact-session-id-here}`

### 5. Inspect the Browser to create a CSR Query 
- On the Analyzer Report for CSRs Today - Inspect the report - Right Click > Inspect.
- Go to the network tab > Refresh > Search for a request in the format: `dataQuery?GET_DATA=`
- Look at the response.
- Copy this response out into a text editor.
- Name the file analyzer.json
- Copy the content after the `query: { ... }` tags

Example:

```javascript
"query": {
			"anchorId": "11894",
			"dateBegin": [
				1612155600000
			],
			"dateEnd": [
				1612328400000
			],
			"timezone": "America/New_York",
			"numberOfRecords": 1000000,
			"lastNRecords": false,
			"activityType": "INTERACTION",
			"aggregateQueryProperties": {
				"computeInterval": 0,
				"computeIntervalUnit": "NONE",
				"lookbackCount": 0,
				"frequency": 0,
				"movingWindow": false,
				"cumulative": false,
				"rowSegmentSet": [],
				"columnSegmentSet": [],
				"queryType": "TEMPORAL",
				"requestType": "PROFILE",
				"intervalAxis": "ROW",
				"computeSummaries": true
			},
			"aggregations": [
				{
					"id": 0,
					"filterGroups": [
						{
							"operator": "AND",
							"valueFilters": []
						}
					],
					"aggregationType": "VALUE",
					"computeColumnName": "sid"
				}
			]
		}

```
### 6 .Copy only the content after `query` and before the ending braces. I.e this content as an example**

```javascript
{
			"anchorId": "11894",
			"dateBegin": [
				1612155600000
			],
			"dateEnd": [
				1612328400000
			],
			"timezone": "America/New_York",
			"numberOfRecords": 1000000,
			"lastNRecords": false,
			"activityType": "INTERACTION",
			"aggregateQueryProperties": {
				"computeInterval": 0,
				"computeIntervalUnit": "NONE",
				"lookbackCount": 0,
				"frequency": 0,
				"movingWindow": false,
				"cumulative": false,
				"rowSegmentSet": [],
				"columnSegmentSet": [],
				"queryType": "TEMPORAL",
				"requestType": "PROFILE",
				"intervalAxis": "ROW",
				"computeSummaries": true
			},
			"aggregations": [
				{
					"id": 0,
					"filterGroups": [
						{
							"operator": "AND",
							"valueFilters": []
						}
					],
					"aggregationType": "VALUE",
					"computeColumnName": "sid"
				}
			]
}
```

### 7. Encode this in a URL encoded format. i.e Copy this string and paste it in an encoder.
Example: 
https://meyerweb.com/eric/tools/dencoder/ 

- Click Encode 

It will give you this text.

```
%7B%0A%09%09%09%22anchorId%22%3A%20%2211894%22%2C%0A%09%09%09%22dateBegin%22%3A%20%5B%0A%09%09%09%091612155600000%0A%09%09%09%5D%2C%0A%09%09%09%22dateEnd%22%3A%20%5B%0A%09%09%09%091612328400000%0A%09%09%09%5D%2C%0A%09%09%09%22timezone%22%3A%20%22America%2FNew_York%22%2C%0A%09%09%09%22numberOfRecords%22%3A%201000000%2C%0A%09%09%09%22lastNRecords%22%3A%20false%2C%0A%09%09%09%22activityType%22%3A%20%22INTERACTION%22%2C%0A%09%09%09%22aggregateQueryProperties%22%3A%20%7B%0A%09%09%09%09%22computeInterval%22%3A%200%2C%0A%09%09%09%09%22computeIntervalUnit%22%3A%20%22NONE%22%2C%0A%09%09%09%09%22lookbackCount%22%3A%200%2C%0A%09%09%09%09%22frequency%22%3A%200%2C%0A%09%09%09%09%22movingWindow%22%3A%20false%2C%0A%09%09%09%09%22cumulative%22%3A%20false%2C%0A%09%09%09%09%22rowSegmentSet%22%3A%20%5B%5D%2C%0A%09%09%09%09%22columnSegmentSet%22%3A%20%5B%5D%2C%0A%09%09%09%09%22queryType%22%3A%20%22TEMPORAL%22%2C%0A%09%09%09%09%22requestType%22%3A%20%22PROFILE%22%2C%0A%09%09%09%09%22intervalAxis%22%3A%20%22ROW%22%2C%0A%09%09%09%09%22computeSummaries%22%3A%20true%0A%09%09%09%7D%2C%0A%09%09%09%22aggregations%22%3A%20%5B%0A%09%09%09%09%7B%0A%09%09%09%09%09%22id%22%3A%200%2C%0A%09%09%09%09%09%22filterGroups%22%3A%20%5B%0A%09%09%09%09%09%09%7B%0A%09%09%09%09%09%09%09%22operator%22%3A%20%22AND%22%2C%0A%09%09%09%09%09%09%09%22valueFilters%22%3A%20%5B%5D%0A%09%09%09%09%09%09%7D%0A%09%09%09%09%09%5D%2C%0A%09%09%09%09%09%22aggregationType%22%3A%20%22VALUE%22%2C%0A%09%09%09%09%09%22computeColumnName%22%3A%20%22sid%22%0A%09%09%09%09%7D%0A%09%09%09%5D%0A%7D
```

### 8. Plug this into the query parameters. Execute the Query

For example, the query is : 

**https://rest.wxcc-us1.cisco.com/aws/api/csrs?q=`your_query_here`**

i.e 

**https://rest.wxcc-us1.cisco.com/aws/api/csrs?q=`%7B%0A%09%09%09%22anchorId%22%3A%20%2211894%22%2C%0A%09%09%09%22dateBegin%22%3A%20%5B%0A%09%09%09%091612155600000%0A%09%09%09%5D%2C%0A%09%09%09%22dateEnd%22%3A%20%5B%0A%09%09%09%091612328400000%0A%09%09%09%5D%2C%0A%09%09%09%22timezone%22%3A%20%22America%2FNew_York%22%2C%0A%09%09%09%22numberOfRecords%22%3A%201000000%2C%0A%09%09%09%22lastNRecords%22%3A%20false%2C%0A%09%09%09%22activityType%22%3A%20%22INTERACTION%22%2C%0A%09%09%09%22aggregateQueryProperties%22%3A%20%7B%0A%09%09%09%09%22computeInterval%22%3A%200%2C%0A%09%09%09%09%22computeIntervalUnit%22%3A%20%22NONE%22%2C%0A%09%09%09%09%22lookbackCount%22%3A%200%2C%0A%09%09%09%09%22frequency%22%3A%200%2C%0A%09%09%09%09%22movingWindow%22%3A%20false%2C%0A%09%09%09%09%22cumulative%22%3A%20false%2C%0A%09%09%09%09%22rowSegmentSet%22%3A%20%5B%5D%2C%0A%09%09%09%09%22columnSegmentSet%22%3A%20%5B%5D%2C%0A%09%09%09%09%22queryType%22%3A%20%22TEMPORAL%22%2C%0A%09%09%09%09%22requestType%22%3A%20%22PROFILE%22%2C%0A%09%09%09%09%22intervalAxis%22%3A%20%22ROW%22%2C%0A%09%09%09%09%22computeSummaries%22%3A%20true%0A%09%09%09%7D%2C%0A%09%09%09%22aggregations%22%3A%20%5B%0A%09%09%09%09%7B%0A%09%09%09%09%09%22id%22%3A%200%2C%0A%09%09%09%09%09%22filterGroups%22%3A%20%5B%0A%09%09%09%09%09%09%7B%0A%09%09%09%09%09%09%09%22operator%22%3A%20%22AND%22%2C%0A%09%09%09%09%09%09%09%22valueFilters%22%3A%20%5B%5D%0A%09%09%09%09%09%09%7D%0A%09%09%09%09%09%5D%2C%0A%09%09%09%09%09%22aggregationType%22%3A%20%22VALUE%22%2C%0A%09%09%09%09%09%22computeColumnName%22%3A%20%22sid%22%0A%09%09%09%09%7D%0A%09%09%09%5D%0A%7D`**


### 9. Add an Accept Header of text/csv
- Add another header of `Accept` `text/csv` to get the raw CSR data from Analyzer.

    `Accept:` `text/csv`

## Part 2: Fetching CARs

<iframe width="560" height="315" src="https://www.youtube.com/embed/PSTexkK2cxs" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Important Links**

> Control hub - For your Org Id: https://admin.webex.com

> Portal: https://portal.wxcc-us1.cisco.com/portal

> Analyzer: https://analyzer.wxcc-us1.cisco.com/analyzer/home

> Legacy V1.0 endpoint - Resource: https://rest.wxcc-us1.cisco.com/aws/api/{record-type}/{id}

> Legacy V1.0 endpoint - Query: https://rest.wxcc-us1.cisco.com/aws/api/{record-type}?q={your-query}

### 1. Understand Contact Start and Contact End Timestamps are in Unix/ Epoch format
- Epoch time for fields `cstts` and `cetts` can be understood my looking at the Epoch converter https://www.epochconverter.com/ 

### 2. Copy the Same CSR Request GET CSR Request and tweak it to a CAR request.
- A CAR is in the format : https://rest.wxcc-us1.cisco.com/aws/api/cars/{session}-{timestamp}-{event}

- Session : CSR
- Timestamp : The `cstts` Contact start time stamp of the event
- Event: the event name: `new`, `ivr-connected`, `parked`, `ended` etc.

Few examples: 

https://rest.wxcc-us1.cisco.com/aws/api/cars/74d98c29-39b4-4e1e-81fa-0ce0ae5aebb0-1612238768144-new

https://rest.wxcc-us1.cisco.com/aws/api/cars/74d98c29-39b4-4e1e-81fa-0ce0ae5aebb0-1612238769933-ivr-connected

https://rest.wxcc-us1.cisco.com/aws/api/cars/74d98c29-39b4-4e1e-81fa-0ce0ae5aebb0-1612238790724-parked

> Substitute your values by Chaining the activity event types like `new` > `ivr-connected` > `parked` and retrieve the `cetts` for those events to plug in the epoch time stamps.

### 3. Complete Building out the above requests.
- Understand that you can start the Analyzer request chain by pulling a CSR report.
- From there, you can fetch the list of CSRs.
- For Each CSR, you can pull the details of every CAR that is an activity within the session.
- Every CAR has a reference to the CSR.

## Part 3: New Webex Contact Center APIs - Retrieving Tasks and Call Recordings

<iframe width="560" height="315" src="https://www.youtube.com/embed/jThcPefuzTA" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Important Links**

> Control hub - For your Org Id: https://admin.webex.com

> Portal: https://portal.wxcc-us1.cisco.com/portal

> Analyzer: https://analyzer.wxcc-us1.cisco.com/analyzer/home

> Developer Portal Docs (Staging): https://apim-dev-portal.appstaging.ciscoccservice.com/

> Developer Webex Documentation: https://developer.webex.com/

> New Webex Contact Center API endpoints: https://webexapis.com/v1/contactCenter/{endpoint}

### 1. Login to developer.webex.com > Documentation > API Reference > Contact Center
- Go to the Get Tasks section.
- Fetch all the tasks using the "From Date/time" in Epoch milliseconds.
- To get the Epoch time use : https://www.epochconverter.com/ 

### 2. Fetch the Tasks from yesterday or the last week - depending on the number of contacts that came in
- Follow the steps to fetch all the contact information.

The same request can be drafted on Postman using your Bearer Token.

Example of a GET Task: 

> https://webexapis.com/v1/contactCenter/tasks?from=__&channelTypes=telephony&orgId=____

> curl --location --request GET '/tasks?channelTypes=&from=&to=&pageSize=&orgId=' \
--header 'Authorization: Bearer YOUR_AUTHORIZATION_TOKEN' 

> `Authorization:` `Bearer your-bearer-token-from-dev-portal`

### 3. Use the following Body for a POST Captures query. Ensure you have includeSegments set to true.

POST https://webexapis.com/v1/contactCenter/captures/query

```javascript
{
        "orgId": "93912f11-6017-404b-bf14-5331890b1797",
        "taskIds": ["6a64d539-4653-4c48-98d7-78fb66c1bc1d", "9dd4a070-4047-46ac-abec-942f48f5535e"],
        "urlExpiration": 30,
        "includeSegments": true
    }

```

### 4. Use the links from the response to download the recordings. 

- If you are doing this programmatically, iterate over all the call recording objects and send a GET request to the call recording target.

Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Arunabh Bhattacharjee (arubhatt) | 2 Feb 2021 |

