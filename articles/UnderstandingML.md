# Understanding Machine Learning
[<img src="https://images.unsplash.com/photo-1503642551022-c011aafb3c88?dpr=2&auto=format&fit=crop&w=1080&h=720&q=80&cs=tinysrgb&crop=">](
https://unsplash.com/photos/2vmT5_FeMck)
Photo by Denys Nevozhai on Unsplash - https://unsplash.com/photos/2vmT5_FeMck


## 📄 Table of contents

  - [What is Machine Learning (ML)](#what-is-machine-learning-ml)
  - [The learning process](#the-learning-process)
      - [1. Asking questions](#1-asking-questions)
      - [2. Iterate](#2-iterate)
  - [ML concepts](#ml-concepts)
      - [Data preprocessing with supervised learning](#data-preprocessing-with-supervised-learning)
      - [Problems](#problems)
      - [Algorithms](#algorithms)
      - [Training the model](#training-the-model)


---
>"A wise man can learn more from a foolish question than a fool can learn from a wise answer." - Bruce Lee
---

## What is Machine Learning (ML)

ML finds patterns in data and uses them to predict the future.

Learning requires:
- identifying patterns
- recognizing those patterns

Now it's easy to find patterns. But it is not easy to find patterns that are correct. Increasing the size of data allows to predict outcome that is more and more correct.

|Data|Algorithm|Model|Application|
|-|-|-|-|
|contains patterns|finds patterns|recognizes patterns|uses to recognition on other data|

Common programming languages used for ML are:
- R
- Python

## The learning process

#### 1. Asking questions

- what questions to ask 
- what data helps you to answer the question
- how do you measure success

#### 2. Iterate

- select and prepare your data over and over to make it useable for the algorithm
- apply an algorithm on the data and create models over and over to increase your success rate
- expose and test successful models to different data

## ML concepts 

- supervised learning (the value you want to predict is already in the data)
- unsupervised learning (the value you want to predict is not in the data)

#### Data preprocessing with supervised learning

Raw data has to be transformed in to training data by removing unnecessary items like duplicates, wrong/false information, useless information. 

The training data contains features, which stand for important classifications and target values, which stand for the desired piece of information for the model.

#### Problems

- regressions (trying to find a line or curve that fit the data)
- classification (trying to group data into classes)
- clustering (trying to identify segments of the data)

#### Algorithms

Common styles are:
- decision trees (construct a model based on actual values of attributes in a data)
- neural networks (construct a model based on the recombination and reevaluation of results within the training data)
- bayesian (filters according to probabilistic classifiers)
- K-means (construct a model based on vector quantization to the *k* closest training examples)

#### Training the model

1. find features that are relevant to identifying the target value
1. put a significant percentage of the features data into the algorithm
1. generate a model
1. test the model with the remaining percentage of the features data by comparing the target values with the values form the actual data
1. if the model is not accurate, change the features, change the algorithm or change the data


Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
