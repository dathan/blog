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

### What the problem really translates to is solved by products
1. Need a notification service to trigger each stage.
2. Start WORK
   1. Is this job a duplicate, 
   2. is it running, 
   3. can the worker run on the same dataset without being descructive
   4. Grab a file from se3
      1. is the network up
      2. are the credenticals correct
      3. can the worker signal when the file is downloaded
      4. is the signal recieved
   5. Process the file
      1. is the network up
      2. is the api available
      3. can the state machiene be set to processed?
   6. Upload the file generated to the correct bucket
      1. is the network up
      2. is state correct
      3. is the database up
      4. are the credentials correct
      5. did the upload succeed
      6. can the state machiene be set to uploaded?
3. Update the database that the file has been processed.
   1. error and state check ....
4. Poll for more work 
   1. error and state check ...


A workflow engine allows you to just work on the buisness logic where retries and handling error are common to the engine.


### To validate the solution

The product requires a summary of video content, this is achieved by getting the raw file, using an api to generate text from spoken tracks in a consistent format.

* Currently can use Deepgram and or openai

