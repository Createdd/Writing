# Natural Language Processing with Python

[<img src="https://images.unsplash.com/photo-1493492473127-f5b4cafeb0b1?dpr=1&auto=compress,format&fit=crop&w=2551&h=&q=80&cs=tinysrgb&crop=">](
https://unsplash.com/photos/iIV0PUqhs00)
Photo by Warren Wong on Unsplash - https://unsplash.com/photos/iIV0PUqhs00


[Open Source Code on Github](asdfasdf)



## 📄 Table of contents
<!-- TOC -->

- [Natural Language Processing with Python](#natural-language-processing-with-python)
  - [📄 Table of contents](#📄-table-of-contents)
  - [Intro](#intro)
    - [Challenges in NLP](#challenges-in-nlp)
    - [Machine Learning Workflow](#machine-learning-workflow)
  - [Auto summarizing texts](#auto-summarizing-texts)
    - [Method Abstract Extraction](#method-abstract-extraction)
  - [Classify text with machine learning](#classify-text-with-machine-learning)
    - [Connecting machine learning to the articles](#connecting-machine-learning-to-the-articles)
    - [Classification](#classification)
  - [Useful links & credits](#useful-links--credits)

<!-- /TOC -->

---
>❝The limits of my language are the limits of my world.❞
‒ Ludwig Wittgenstein
---

## Intro

### Challenges in NLP

- Tokenization (breaking text into smaller pieces)
- Stopword Removal (Filtering non-important words)
- N-Grams (Grouping related words)
- Word Sense Disambiguation (Identifying the context in which the word occurs)
- Parts-of-Speech (Identifying characteristics of a language)
- Stemming (Removing endings of words)

### Machine Learning Workflow

1. Pick a problem
1. Represent data using numeric attributes
1. Use an algorithm to find a model


## Auto summarizing texts

### Method Abstract Extraction

- find the most important words (important words are generally more often repeated)
- calculate a score for sentences containing important words 
- select import sentences

## Classify text with machine learning

### Connecting machine learning to the articles

- Divide the articles into groups based on some common attributes (clustering) -> we want to maximize intracluster similarity
- Use [tf-idf](https://en.wikipedia.org/wiki/Tf%E2%80%93idf) to find important words in an article and represent those documents 
- apply the K-Means Clustering technique, by setting centers of the cluster, assigning each point to the center and rearrange the center of the cluster over again until the means do not change anymore
- 

### Classification
To apply any machine learning we need data. The data will be a set of articles. 

In those articles a certain theme will be identified. Those themes will be assigned to the new articles. 

For a new article a resulting model will be used and applies a theme.





## Useful links & credits
- [📄 "Begin"](afgafgadgads)



Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
