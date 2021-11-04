---
title: 'Lab 2(c): Flow Debugging Flows'
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/Hi6cGSSrswU" title="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents

- Overview Of Flow Debugging
- Enabling Debug logs
- Accessing the flow
- Accessing the logs


# Introduction

## Lab Objective

This document helps to understand flow debugging concepts.

## Pre-requisite

1. Admin credentials to login to Control Hub and WxCC administration portal.

# Overview Of Flow Debugging

## 1. Enabling Debug logs

- By default only standard logs will be enabled.
- In order to enable debug logs to see the complete HTTP request and response, Click on settings icon from top right.
- Enable the toggle 'descriptive logs'.

## 2. Accessing the flow

- Select the service that contains the flow you would like to debug.
- On the list of flows, go to the flow in question.
- Under actions click on 'arrow' mark and select manage.
- This will bring up flow workspace.


## 3. Accessing the logs

- On the right pane click on debug which will bring up a window at the bottom of the screen
- Each row here represents logging for one task, click on 'decrypt logs' on the right side to see debug logging.
- Click on the trasactionID, you can see nodes that were executed as part of the flow along with node ID's.
For example, click on create conversation, you can see the HTTP request and response cycle on the right.

Please ensure you provide the id in the response body of create task and the transaction ID while opening TAC case.


Changelog:

| **Version** | **Comments** | **Author(s)** | **Date** |
| --- | --- | --- | --- |
| 1.0 | Initial Release | Shrishail (sdoddali@cisco.com) | 31 Oct 2021 |
