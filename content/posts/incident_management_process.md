---
title: "Incident Management Process"
date: 2021-10-26T18:07:05-07:00
draft: false
---


# Goal

Define a runbook of sorts of how to run a common incident response process to ensure that we are working on the right thing, keeping all stakeholders in the loop, assigning focus roles, and getting to the root cause of the incident or at least mitigating the problem.



# What is a P1 incident

An incident is when there is a customer visible outage that interrupts the behavior or functionality of the platform.

## Examples of incidents:

* The Customer is unable to deploy
* The account ran out of nodes to launch
* Certificate expires
* Config Management system is down
* Database is down
# Base Process

[Five whys](https://en.wikipedia.org/wiki/Five_whys) - The primary goal of the technique is to determine the root cause of a defect or problem by repeating the question "Why?"

```
Why? – The battery is dead. (First why)
Why? – The alternator is not functioning. (Second why)
Why? – The alternator belt has broken. (Third why)
Why? – The alternator belt was well beyond its useful service life and not replaced. (Fourth why)
Why? – The vehicle was not maintained according to the recommended service schedule. (Fifth why, a root cause)


```

Note: Please [read](https://www.kitchensoap.com/2012/02/10/each-necessary-but-only-jointly-sufficient/) on why the Five Why's is a good start and there is more.


1. Validate there is a problem and this problem is a P1 Incident as of the ilk described above.
2. Create a Jira Ticket in the IM board
3. Create a Slack war room, slack public channel, and invite all needed to help. You are not alone in an incident, this is not a runbook event, this is an outage affecting customers or members that do not have a response.
4. Announce in #tech-outage
5. Assign Roles
6. Isolate and record experiments by coordinating with the roles of the IM
7. Log for future Post Mortem
8. Update Stakeholders every 15 to 45 minutes 
9.  Log all manual changes
10. Five Whys
11. Verify recovery
12. Announce resolved (Yellow Status)
13. Announce resolved (Green status) when tech-debt is cleaned up after the customer verifies the fix
14. Start Incident Report
15. Schedule a Post Mortem



# Roles

*Communicator* - This role requires the person to give updates, even if there are none to the stakeholders’ slack channel(s) any and all updates of the current incident 

*Recorder* - An incident document is created after the base Jira procedure is followed, a log of sorts of what is tried and did not work

*Lead* - The lead works with the communicator and the Team coordinating different ICs to try distinct experiments to determine the root cause of the incident.

*IC* - The end engineer working on the problem, coordinating with the lead and other ICs to ensure that the experiments do not interfere with other ICs and are recorded by the recorder.


Follow the incident response process by focusing on what we are fixing, what is broken, and how data-did or did not verify our assumptions. We follow an experiment process described below, whilst communicating what step of the experiment you are at with the team.

![Scientific Method](/blog/img/process.png)


Finally use observability tools to identify symptoms to narrow down on the cause. Data should back experiment direction and conclusion to narrow down the problem.

Think of the problem like a bomb exploding. Now when the bomb exploded you look at the debris first and take inventory of the damage. Start expanding the blast radius's scope and add more things involved in the blast radius. This is a measured divide and conquer of sorts where the problem is being defined incrementally as a path is traveled when there is enough data, stop or look elsewhere. The goal is to be disciplined, measured, and stop the rush of "pushing many different buttons" to rush to a fix.

# RCA Followup

RCA stands for root cause analysis, this is the executive summary meeting for what the root cause was. Here is a format, and a supporting document to back up the format.

## Meeting Format
1. Introduction (5-10 minutes)
> Welcome and introductions
> Purpose and objective of the meeting
> Ground rules

2. Background and Problem Description (10-15 minutes)
> Brief description of the complex system
> Details of the failure
> Impact on organization, customers, etc.

3. Initial Analysis (15-20 minutes)
> Timeline of events leading to failure
> Initial findings and observations
> Overview of data and evidence collected

4. Root Cause Analysis (30-60 minutes)
> Identification of potential root causes (use techniques like Fishbone Diagram, 5 Whys, etc.)
> Discussion and deep dive into potential root causes
> Validation of root causes

5. Action Planning (15-30 minutes)
> Proposed solutions or corrective actions
> Timeline for implementation
> Assignment of responsibilities

6. Conclusion and Follow-Up (5-10 minutes)
> Summary of key findings and decisions
> Schedule follow-up meetings or status updates
> Closing remarks

## Document Format
A comprehensive document should be prepared to capture all the details from the RCA meeting. Here's a recommended format:


### Title Page
> Title: Root Cause Analysis for [Failure/System]
> Date
> Author/Team
> Confidentiality Note if required


### Executive Summary
> Brief overview of the issue and key findings

### Table of Contents

1. Introduction
> Background of the complex system
> Objectives of the RCA

2. Scope
> What is in Scope and not in scope, to support what the problem was

4. Problem Description
> Detailed description of the failure
> Impact and significance
> Supporting evidence and data

4. Methodology
> RCA approach and methods used (e.g., Fishbone Diagram, 5 Whys, etc.)
> Teams and stakeholders involved

5. Analysis
> Detailed analysis of potential root causes
> Validation and justification of identified root causes

6. Recommendations
> Corrective actions
> Preventive measures
> Timeline and responsibilities

7. Conclusion

### Summary and final thoughts
### Appendices
### Supporting documents, diagrams, charts, etc.
### Acknowledgments
### Revision History



This format ensures that the RCA is thoroughly analyzed and documented, providing a clear and actionable path forward to address the failure.



# Resources 

https://en.wikipedia.org/wiki/Five_whys

https://www.kitchensoap.com/2012/02/10/each-necessary-but-only-jointly-sufficient/

https://courses.lumenlearning.com/boundless-psychology/chapter/the-scientific-method/



