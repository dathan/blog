---
title: "Journal Tasks Log 6"
date: 2023-03-08T13:20:33-08:00
draft: false
---

# What problem am I trying to solve

Extract content from a dailyco + deepgram session realtime


# What am I trying to do to solve the probkem

- Display the transcription realtime
    - display the user and what they said
        - display the avatar The avatar has a tooltip of the username
    - make the body transparent and lighten up the boxes

- Summarize the transcription like a CNN key takeway of a speech.
    - buffer the messages, once the messages hit a threshold
        - empty the buffer 
        - AI Summarize
        - fill the display buffer

# What is the priority
 - Display --> 1d and will require big changes
 - Summarize --> 1d an minor changes


# What am I going to do
- scope this to development ✅
- display the avatar ✅
- on meeting join and isOwner start transcribing ✅
- show the transcription button for clients ✅


Just finished the ~~design~~ buildingof a real-time transcription summary service for meetings. A Note feature where you don't have to take notes. Each chunk of time will link to the timeslice summarized. I have the transcription and summary working. Now trying to make this look good. 
