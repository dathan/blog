---
title: "Vector Embeddings"
date: 2023-04-04T18:39:12-07:00
draft: false
---


## What are Vector Embeddings 


Let's go back to the number line. The distance between two points; This is a good example of what Vector Embeddings are, fingerprinting a document into a number in multi-dimensional space. Since a document can be represented as a number (series of numbers), now a relation can be made between two documents. The relation in terms of distance between two vectors (which could be a markdown document for instance), small distances have a high relatedness and large distances suggest a low relatedness.

Since a number represents the document, semantic similarity can be used. The semantic similarity, which we as humans take for granted can be represented in vector space. So instead of 2d space, we use 1000s of dimensions.

A good write-up is the 1st Google result by pinecone.io https://www.pinecone.io/learn/vector-embeddings/


This means the following algorithm will work

1. Encode your document using openai embeddings, and use a cosine curve to match later.
2. store the embedding in Redis
3. A web app asks a question.
4. The query is matched against redis, take the top result
5. feed that result to openai along with the question in 3.


Now you have a chat experience on matching data, which is most likely not in the 2022 index that chatgpt has.



I am currently writing a GO program to help me illustrate this.
https://github.com/dathan/go-vector-embedding


## Resources 

- https://github.com/openai/openai-cookbook/blob/main/text_comparison_examples.md

- https://openai.com/blog/introducing-text-and-code-embeddings/

- https://openai.com/blog/new-and-improved-embedding-model/

- https://huggingface.co/spaces/mteb/leaderboard

- https://github.com/openai/openai-cookbook/blob/main/examples/Semantic_text_search_using_embeddings.ipynb (example search)
- https://github.com/openai/openai-cookbook/blob/main/examples/Question_answering_using_embeddings.ipynb
- https://github.com/openai/openai-cookbook/blob/main/examples/Customizing_embeddings.ipynb



## Check back, I'll be updating this soon

Thanks for reading!
