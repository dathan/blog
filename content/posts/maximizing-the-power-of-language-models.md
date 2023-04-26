---
title: "Maximizing the Power of Language Models: Prompt Engineering"
date: 2023-03-22T14:34:34-07:00
draft: false
---


# What is Prompt Engineering


Let's ask chat gpt:


![chatgptresult](/blog/img/what-is-promp-engineering.png)

### Response in text

>Prompt engineering is the practice of crafting effective prompts to generate specific outputs from language models like LLMs (Large Language Models). It involves selecting the appropriate vocabulary, formatting, and instructions to help the model understand the desired task and generate the desired output.

>Effective prompts can improve the performance of LLMs in various natural language processing tasks, such as language translation, sentiment analysis, text summarization, and language generation.

>Here are some examples of prompts that prompt engineers may use to get the most out of a LLM:

>Translation: For language translation, a prompt may include the source language text and instructions to generate the corresponding translated text in the target language. For example, a prompt for translating a French sentence to English may look like this: "Translate the following French sentence into English: 'Le chat noir saute sur la table.'"

>Summarization: For text summarization, a prompt may include a long document and instructions to generate a brief summary. For example, a prompt for summarizing an article about climate change may look like this: "Provide a one-paragraph summary of the following article on climate change: [Insert article text]."

>Sentiment analysis: For sentiment analysis, a prompt may include a sentence or a paragraph and instructions to determine the sentiment expressed. For example, a prompt for analyzing the sentiment of a customer review may look like this: "Determine the sentiment of the following customer review: 'The product was excellent and exceeded my expectations.'"

>Text generation: For text generation, a prompt may include a few sentences and instructions to generate a coherent and relevant continuation. For example, a prompt for generating a news article may look like this: "Write a news article about the recent election results in [insert country], including the following details: [insert details]."

>In general, effective prompts should be specific, concise, and tailored to the desired output. By using well-crafted prompts, prompt engineers can enhance the capabilities of LLMs and improve their accuracy and efficiency in various natural language processing tasks.


## So how can I use this in my code, how can I be a prompt engineer?

As an engineer, college English classes now make sense. I remember that I would lament, "Why do I have to read these books, I'll never have to apply this for the work I am going to do."

I was wrong, I have used the full skills learned in college throughout my career. The time that I spent writing many reports in English, my blog posts, and my communication with engineers, have all been augmented and perfected by my college English courses. That knowledge now is more important than ever. Now I can use my engineering skills, English skills, critical thinking skills, and knowledge transfer to build great prompts that enable me to use open-ai gpt to augment applications.



## Okay show me an example

```
For the following transcript summarize, pull out key topics, questions and answers. Return the result in JSON with the following dictionary elements  "summaries, topics, questions-answered, main-points". For each dictionary element return the top 3 of that element as an array:


```

I expect the following return:
`
{
    [
        { 
            summary: [],
            topics: [],
            questions: [],
            main points: [],
        }
    ]
}


What I received was the following:


```
{
   "summaries":[
      "Troy Malone, a former executive in different tech companies, shares his experiences in the tech industry from being an investor to builder and the lessons he learned along the way. He discusses his failed startup and how it helped him develop the skills to succeed in his current job at Evernote, where he helped take the company into the Asian market.",
      "Troy Malone, a former executive in different tech companies, shares his experiences in the tech industry from being an investor to builder and the lessons he learned along the way. He discusses his failed startup and how it helped him develop the skills to succeed in his current job at Evernote, where he helped take the company into the Asian market.",
      "Troy Malone shares his experiences in the tech industry, from being an investor to builder and the lessons he learned along the way, including his failed startup and how it helped him develop the skills to succeed in his current job at Evernote. He talks about taking Evernote into the Asian market, where the company had great metrics and user growth."
   ],
   "topics":[
      "Tech industry experiences",
      "Failed startup",
      "Lessons learned",
      "Success at Evernote",
      "Taking Evernote into Asian market",
      "User growth"
   ],
   "questions-answered":[
      "What was Troy Malone's experience in the tech industry?",
      "What did Troy Malone learn from his failed startup?",
      "What company did Troy Malone help take into the Asian market?",
      "What were the metrics and user growth of the company Troy Malone helped take into the Asian market?"
   ],
   "main-points":[
      "Troy Malone was an executive in various tech companies.",
      "He transitioned from investor to builder and learned a lot from his experiences.",
      "He started a company in 2008 that failed, but it helped him develop skills that led to his success at Evernote.",
      "Troy helped take Evernote into the Asian market, where the company had great metrics and user growth."
   ]
}
```

from the following YouTube Video

[https://www.youtube.com/watch?v=HaLZcaDfaVY](https://www.youtube.com/watch?v=HaLZcaDfaVY)




### Conclusion

Using English to be as specific as possible and formatting the data in a way that you as a programmer can understand and a machine can understand (JSON). You too can become a prompt engineer as an engineer. The last piece of the puzzle to be a prompt engineer is knowing how to code to process this data over an API call and integrate it into an application. Note, if you become good at prompt engineering, the last requirement can be worked around.


