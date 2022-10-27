---
title: "Journal Tasks Log 1"
date: 2022-10-26T13:38:40-07:00
draft: false
---




# Focus


I am trying to build an interface to a tool, that uses google auth, takes some text and summerizes the content to a few bullet points.
Then from these bullet points, build a social post.


## Grief

Today I recieved the official news that my dad has stage 4-5 prostate cancer, thyroid cancer, and most likely bone cancer from the scan. I write this for self-releaf. To remind myself, he is on the other side of the United States, in Maryland. I have so many emotions but this is when I jump into action of sorts. I am trying to coordinate and help my sister who is close to him. I also looked up care.com providers. I still need more info before I execute on the initatives in detail, but at least I have a path.
I write this to let go of the grief I am feeling now, and to acknowlege it, I can do what I can do for now and I need to focus on what my team needs from me.


## Tasks

ordered quickest task 1st from 1st attempt.


1. download transcript from dropbox [3h]
2. process transcript and pull out mentor's responses [2h]
3. store result [1h]
4. cursor through the text by character count, verify last word is a word. [3h]
5. send each chunk to unfriendly endpoint [?? -> see *Tasks HARD*]



## Tasks HARD - talk to google auth endpoint

Goal:
Create an interface to query the consumer app

1. consistent auth but not impossible.
2. submit content to the api endpoint
   1.  curl 'https://i.jasper.ai/functions/api/getCompletion' 
3. parse results and store.



## Some notes

1. (https://github.com/microsoft/playwright/issues/15328#issuecomment-1172963255)[how to log in with google auth and playwrite
