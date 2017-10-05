# Natural Language Processing with Python

[<img src="https://images.unsplash.com/photo-1493492473127-f5b4cafeb0b1?dpr=1&auto=compress,format&fit=crop&w=2551&h=&q=80&cs=tinysrgb&crop=">](
https://unsplash.com/photos/iIV0PUqhs00)
Photo by Warren Wong on Unsplash - https://unsplash.com/photos/iIV0PUqhs00


[Open Source Code on Github](https://github.com/DDCreationStudios/summarizeTextPy)



## 📄 Table of contents
<!-- TOC -->

- [Natural Language Processing with Python](#natural-language-processing-with-python)
  - [📄 Table of contents](#📄-table-of-contents)
  - [Intro](#intro)
    - [Challenges in NLP](#challenges-in-nlp)
    - [Machine Learning Workflow](#machine-learning-workflow)
  - [Theory of summarizing and classifying texts](#theory-of-summarizing-and-classifying-texts)
    - [Method Abstract Extraction](#method-abstract-extraction)
    - [Connecting machine learning to the articles](#connecting-machine-learning-to-the-articles)
    - [Classification](#classification)
  - [Code example](#code-example)
    - [Getting text from a website](#getting-text-from-a-website)
    - [Summarize text](#summarize-text)
    - [Find themes in articles](#find-themes-in-articles)
  - [Useful links & credits](#useful-links--credits)

<!-- /TOC -->

---
>"The limits of my language are the limits of my world."
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


## Theory of summarizing and classifying texts

### Method Abstract Extraction

- find the most important words (important words are generally more often repeated)
- calculate a score for sentences containing important words 
- select import sentences


### Connecting machine learning to the articles

- Divide the articles into groups based on some common attributes (clustering) -> we want to maximize intracluster similarity
- Use [tf-idf](https://en.wikipedia.org/wiki/Tf%E2%80%93idf) to find important words in an article and represent those documents 
- apply the K-Means Clustering technique, by setting centers of the cluster, assigning each point to the center and rearrange the center of the cluster over again until the means do not change anymore
- 

### Classification

A typical classification workflow consists of testing data using numerical attributes, training the model with data and at the end test the model with other test data.

To apply any machine learning we need data. The data will be a set of articles. 

In those articles a certain theme will be identified. Those themes will be assigned to the new articles. 

For a new article the model will be used and applies a corresponding theme.

## Code example

### Getting text from a website

```python
from urllib.request import urlopen
from bs4 import BeautifulSoup

articleURL = "http://curia.europa.eu/juris/document/document.jsf?text=&docid=139407&pageIndex=0&doclang=EN&mode=lst&dir=&occ=first&part=1&cid=52454"

def getText(url):
    page = urlopen(url).read().decode('utf8', 'ignore')
    soup = BeautifulSoup(page, 'lxml')
    text = ' '.join(map(lambda p: p.text, soup.find_all('p')))
    return text.encode('ascii', errors='replace').decode().replace("?","")

text = getText(articleURL)
```


### Summarize text


```python
import nltk
# nltk.download('punkt')
# nltk.download()
from nltk.tokenize import sent_tokenize, word_tokenize
from nltk.corpus import stopwords
from nltk.probability import FreqDist
from collections import defaultdict
from string import punctuation
from heapq import nlargest

def summarize(text, n):
    sents = sent_tokenize(text)
    
    assert n <= len(sents)
    wordSent = word_tokenize(text.lower())
    stopWords = set(stopwords.words('english')+list(punctuation))
    
    wordSent= [word for word in wordSent if word not in stopWords]
    freq = FreqDist(wordSent)

    ranking = defaultdict(int)
    
    for i, sent in enumerate(sents):
        for w in word_tokenize(sent.lower()):
            if w in freq:
                ranking[i] += freq[w]

    sentsIDX = nlargest(n, ranking, key=ranking.get)
    return [sents[j] for j in sorted(sentsIDX)]

summaryArr = summarize(text, 10)
# summaryArr
```


### Find themes in articles

```python
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.cluster import KMeans
import numpy as np

vectorizer = TfidfVectorizer(max_df=0.5,min_df=2,stop_words='english')
X = vectorizer.fit_transform(summaryArr)
km = KMeans(n_clusters = 3, init = 'k-means++', max_iter = 100, n_init = 1, verbose = True)
km.fit(X)
np.unique(km.labels_, return_counts=True)

text={}
for i,cluster in enumerate(km.labels_):
    oneDocument = summaryArr[i]
    if cluster not in text.keys():
        text[cluster] = oneDocument
    else:
        text[cluster] += oneDocument

stopWords = set(stopwords.words('english')+list(punctuation))
keywords = {}
counts={}

for cluster in range(3):
    word_sent = word_tokenize(text[cluster].lower())
    word_sent=[word for word in word_sent if word not in stopWords]
    freq = FreqDist(word_sent)
    keywords[cluster] = nlargest(100, freq, key=freq.get)
    counts[cluster]=freq

uniqueKeys={}
for cluster in range(3):   
    other_clusters=list(set(range(3))-set([cluster]))
    keys_other_clusters=set(keywords[other_clusters[0]]).union(set(keywords[other_clusters[1]]))
    unique=set(keywords[cluster])-keys_other_clusters
    uniqueKeys[cluster]=nlargest(10, unique, key=counts[cluster].get)

print(uniqueKeys)
```



## Useful links & credits
- A great course can be found on [Pluralsight](https://www.pluralsight.com/)

---

Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
