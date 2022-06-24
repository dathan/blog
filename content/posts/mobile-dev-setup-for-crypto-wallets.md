---
title: "Mobile Dev Setup for Crypto Wallets"
date: 2022-01-28T17:45:40-08:00
draft: true
---

For years when interacting with the web you can simulate the mobile experience directly on the desktop. When working with deep-links, click a button on the web, then open a mobile native application assumptions are not the same.

For instance, when working with Metamask and resizing the look and feel from chrome tools to visualize the mobile experience-I am using the behavior of the browser that has a chrome extension that can answer the metamask interaction. The browser on your phone does not have this, thus the behavior is different and getting the look and feel working is mute because that experience is not how things work.


I am changing my metamask flow to be a switch, to switch between wallet-connect, wallet-link and metamask. This will allow me to open a wallet on a mobile device which in most cases is a native application. This expansion will enable mobile to use the application and mint an award for my needs.


Now that I have a problem, let's go with some stuff in my work history on how I would solve the issue that I need to test with my device browser and launch an experience on my device when the webserver runs on my laptop.

The solution that I would first try is Charles Proxy. Here is the setup:

- https://www.charlesproxy.com/documentation/faqs/using-charles-from-an-iphone/

