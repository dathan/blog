---
title: "Maximizing Web Based Sharing for Effective Previews Across Platforms"
date: 2023-02-02T10:02:44-08:00
draft: false
---

## Motivation

I have been writing sharing content on various platforms for quite some time. This is my attempt at recording all the things that I do to effectively share effective Previews across LinkedIn, Facebook, iMessage, Twitter and any other Open Graph compatible system.

## History

The Open Graph protocol was first introduced in 2010 by Facebook. It was created as a way for website owners to better control how their pages were represented when shared on Facebook. The protocol provides a standardized set of meta tags that can be added to a webpage's HTML code, allowing the page to specify details such as its title, description, and image. This allows Facebook (and other social media platforms) to display a more visually appealing and information-rich preview of the page when it's shared. The Open Graph protocol has since become a widely adopted standard, used by many websites to enhance the appearance of their pages when shared on social media.

## Tools for effective OG Tag Testing

### https://developers.facebook.com/tools/debug/

This tool is a must. Facebook created the protocol, facebook is the biggest social network that allows sharing in this mannor, and the tool is intuitive. Additionally Facebook Does heavy caching, show chaning the url with a timestamp is a way to bust it. Also I remember that with the tool you can invalidate the cache, yet I have not validated that in a while.

### https://cards-dev.twitter.com/validator

This was a great tool, but it seems to be removed for some reason try
https://tweetpik.com/twitter-card-validator instead

### https://www.linkedin.com/post-inspector/inspect/

This will just render.

### https://www.opengraph.xyz 

This is great tool but does not simulate the platform correctly

### Slack

This is probably the best client to use. Slack does a great job and renders quickly.

## How to reach your laptop

Each of these tools require a public endpoint for that platform's crawler to fetch. Thus you will need to set up some sort of proxy to your development environment for fast iteration.

My choice setup is `ngrok`. With two commands:

`ngrok config add-authtoken`
`ngrok http 3000` so the public can reach my node demo

## Mimimum requirements to render correctly on a platform
### Basic Tags needed

```html

  <!-- HTML Meta Tags -->
  <title>Prioritization and Time Management for Technical Leadership | Plato Academy</title>
  <meta name="description" content="This Circle is designed to help Technical Leaders of medium-sized companies better prioritize and manage their time. Over the course of four online sessions, participants will be guided through topics such as creating a clear set of goals, managing team workloads, and dealing with unexpected changes. Each session will provide actionable advice and strategies to help Technical Leaders scale their teams successfully.">

  <!-- Facebook Meta Tags -->
  <meta property="og:url" content="https://aa25-73-158-42-46.ngrok.io/circles/prioritization-and-time-management-for-technical-leadership-93vj58i3w5v">
  <meta property="og:type" content="website">
  <meta property="og:title" content="Prioritization and Time Management for Technical Leadership | Plato Academy">
  <meta property="og:description" content="This Circle is designed to help Technical Leaders of medium-sized companies better prioritize and manage their time. Over the course of four online sessions, participants will be guided through topics such as creating a clear set of goals, managing team workloads, and dealing with unexpected changes. Each session will provide actionable advice and strategies to help Technical Leaders scale their teams successfully.">
  <meta property="og:image" content="https://cdn.platohq.com/assets/users/avatars/183f0b10-6a55-4083-aeaf-570a48f26326.jpg">

  <!-- Twitter Meta Tags -->
  <meta name="twitter:card" content="summary_large_image">
  <meta property="twitter:domain" content="aa25-73-158-42-46.ngrok.io">
  <meta property="twitter:url" content="https://aa25-73-158-42-46.ngrok.io/circles/prioritization-and-time-management-for-technical-leadership-93vj58i3w5v">
  <meta name="twitter:title" content="Prioritization and Time Management for Technical Leadership | Plato Academy">
  <meta name="twitter:description" content="This Circle is designed to help Technical Leaders of medium-sized companies better prioritize and manage their time. Over the course of four online sessions, participants will be guided through topics such as creating a clear set of goals, managing team workloads, and dealing with unexpected changes. Each session will provide actionable advice and strategies to help Technical Leaders scale their teams successfully.">
  <meta name="twitter:image" content="https://cdn.platohq.com/assets/users/avatars/183f0b10-6a55-4083-aeaf-570a48f26326.jpg">

  <!-- Meta Tags Generated via https://www.opengraph.xyz -->

```

Above is the end format that needs to be presented to the crawler. It will not execute javascript, thus static data for react projects will be needed to handle this use case. I just learned how to do this in nextjs, and that deserves a post on it's own.


You need the following combo to have an effective post to share:


```html

  <!-- HTML Meta Tags -->
  <title>Prioritization and Time Management for Technical Leadership | Plato Academy</title>

  <meta name="description" content="This Circle is designed to help Technical Leaders of medium-sized companies better prioritize and manage their time. Over the course of four online sessions, participants will be guided through topics such as creating a clear set of goals, managing team workloads, and dealing with unexpected changes. Each session will provide actionable advice and strategies to help Technical Leaders scale their teams successfully.">
```

* All though above is not an OG tag, it is nessasry to have this in your post. Nothing in the spec requires this, but I found crawlers behave funky if basic HTML fields are conflicting with OG meta tags

* `og:type content="website"` - tell the crawler what type of page this is. This will cause format changes in a few sites
* `og:url content="current_page_url"` - this is important, the current page url rule can be ignored and sometimes crawlers will display the wrong Open Graph Content for the current url, due to how the displayer implements their cache.
* `og:image content="cdn_url"` - even if its a basic stock logo image you want to have an image on the display of the post. Its causes more real-estate to be used from the platform provider, increasing the chances of a click.

## Notes on how not everything is the same

### Facebook, Twitter, Imessage, LinkedIn, Slack implement everything differently og:crawl all differently

* Facebook, Twitter cannot have query params over what I think is 255 characters
* Imessage, LinkedIn, Slack are the best platforms that follow the spec without limiting the GET on their crawler arbirarely as of `2023-02-02T10:02:44-08:00`

## Conclusion

I want to push out this post, there is a lot of things that I am neglecting to mention. I will add them here over time. Check back soon :) 
