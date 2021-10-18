---
title: "Rituals in DevOps for Teams"
date: 2021-10-18T11:38:59-07:00
draft: false
---
Every Monday, leadership pass downs happen, then we have a standup, then we talk about the pages of the past week. To aid in this ritual, we have an automated Confluent Page, generated from a cronjob that documents all the PagerDuty's pages. The program reads data over PagerDuty's API and writes to Confluence API running as a cronjob in Kubernetes.

These actions described since performed at a regular cadence is a ritual. Performing it generated a thought about rituals and how rituals can have a profound impact on the running of a system when performed by a team. 

The rituals we follow on my team are classified into observations and social communication. For what I am calling observations, weekly we review the past pages for the previous week. Then for social communication, we pass down what we learned from the pages of the past week and how that pages were resolved. We also verify the effect of the recovery with changes visualized over time using Grafana dashboards.

I have been doing this process for over two years. The teams have steadily increased shared knowledge and built a consistent mechanism of sharing that knowledge of what to do for a specific incident. The other side of this ritual that does not get much attention is the by-products produced by the ritual for later referral. The documentation produced as a result of talking about the past incident is key for discovery about what to do in a future similar incident. This content creation allows a future engineer to search for a problem in the internal system and either find a runbook and or find the breadcrumbs to the past mitigation to produce a possible runbook. 

Thus rituals are required, beneficial, and aligns a team to the common narrow focus of getting these things to stop paging us and as a result, make the system more resilient.

#### Notes

` The Team does the same thing collectively at the same time on a reoccurring basis and talks about it` *==* `RITUALS`