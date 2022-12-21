---
title: "Data Pipeline Thoughts"
date: 2022-12-21T08:03:03-08:00
draft: true
---



I have always run into the need to perform a [workflow](https://github.com/meirwah/awesome-workflow-engines), and there is a lot of engines that enable workflows out there. But for the basics, writing a program and checking the state at each stage is how I will solve my current need.

Some keywords for the space: BPMN - Buisness Process Management


### Problem

1. Poll Queue for work
1. START WORK
    1. Grab a file from s3
    1. Process that file from s3 against an API
    1. Upload the file generated to s3
1. Update the database that work is done


### To validate the solution

The product requires a summary of video content, this is achieved by getting the raw file, using an api to generate text from spoken tracks in a consistent format.

* Currently can use Deepgram and or openai

