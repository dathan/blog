---
title: "Chat with GPT-4 & Save Prompts/Responses to Git"
date: 2023-03-29T21:42:15-07:00
draft: false
---


# Saw an ask on Twitter
A person I follow on Twitter tweeted:
> Is there a git/version control for prompts? I hate losing great prompts and I’d love to be able to iterate on them.

## So I created a quick command line chat to GPT-4

https://github.com/dathan/go-openai-prompt-git-save

It is a go program, and you need an OPENAI Token and a GitHub User Token in your environment. The program is very simple. From the terminal, have a chat interface to OpenAi, and save the prompts asked, to GitHub, with the content from GPT-4's response.

The data get stored on GitHub. If the repo does not exist, it will create it. The program just appends every prompt and the prompts return then commits the changes to git, then pushes the changes to GitHub.

Now you can always keep your prompts.

Here are some prompts I have

https://github.com/dathan/openai-prompts-save/blob/master/prompts.md


## This is an MVP

This program was quickly put together and can be optimized. For instance, the commit to git can be asynchronous but I need to ensure that all the prompts go into a worker pool since the clone happens on every save. Also, I could just memorize the initial clone and reuse it.

That being said, for 3 hours of work it works!

### Some musings

Google has an API to GitHub and created the go package, which is pretty cool.
