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


[![img](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Reinforcement_learning_diagram.svg/300px-Reinforcement_learning_diagram.svg.png)](https://en.wikipedia.org/wiki/Reinforcement_learning#/media/File:Reinforcement_learning_diagram.svg)

By <a href="//commons.wikimedia.org/w/index.php?title=User:Megajuice&amp;action=edit&amp;redlink=1" class="new" title="User:Megajuice (page does not exist)">Megajuice</a> - <span class="int-own-work" lang="en">Own work</span>, <a href="http://creativecommons.org/publicdomain/zero/1.0/deed.en" title="Creative Commons Zero, Public Domain Dedication">CC0</a>, <a href="https://commons.wikimedia.org/w/index.php?curid=57895741">Link</a>



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

[![img](https://upload.wikimedia.org/wikipedia/commons/f/f3/CART_tree_titanic_survivors.png)](https://commons.wikimedia.org/w/index.php?curid=14143467)

By Stephen Milborrow - Own work, CC BY-SA 3.0


- neural networks (construct a model based on the recombination and reevaluation of results within the training data)
[![img](https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Colored_neural_network.svg/296px-Colored_neural_network.svg.png)](https://commons.wikimedia.org/w/index.php?curid=24913461)

By Glosser.ca - Own work, Derivative of File:Artificial neural network.svg, CC BY-SA 3.0,

- bayesian (filters according to probabilistic classifiers)


[![img](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/SimpleBayesNet.svg/1150px-SimpleBayesNet.svg.png)](https://en.wikipedia.org/wiki/Bayesian_network#/media/File:SimpleBayesNet.svg)

- K-means (construct a model based on vector quantization to the *k* closest training examples)

[![img](https://upload.wikimedia.org/wikipedia/commons/thumb/1/10/Iris_Flowers_Clustering_kMeans.svg/660px-Iris_Flowers_Clustering_kMeans.svg.png)](https://en.wikipedia.org/wiki/K-means_clustering#/media/File:Iris_Flowers_Clustering_kMeans.svg)
Iris flower data set, clustered using k means (left) and true species in the data set (right). Note that k-means is non-determinicstic, so results vary. Cluster means are visualized using larger, semi-transparent markers. The visualization was generated using ELKI.


#### Training the model



1. find features that are relevant to identifying the target value
1. put a significant percentage of the features data into the algorithm
1. generate a model
1. test the model with the remaining percentage of the features data by comparing the target values with the values form the actual data
1. if the model is not accurate, change the features, change the algorithm or change the data


[![img](https://upload.wikimedia.org/wikipedia/commons/thumb/5/54/Generic_Michigan-style_Supervised_LCS_Schematic.png/1920px-Generic_Michigan-style_Supervised_LCS_Schematic.png)](https://en.wikipedia.org/wiki/Learning_classifier_system#/media/File:Generic_Michigan-style_Supervised_LCS_Schematic.png)
By <a href="//commons.wikimedia.org/w/index.php?title=User:Docurbs&amp;action=edit&amp;redlink=1" class="new" title="User:Docurbs (page does not exist)">Docurbs</a> - <span class="int-own-work" lang="en">Own work</span>, <a href="http://creativecommons.org/licenses/by-sa/4.0" title="Creative Commons Attribution-Share Alike 4.0">CC BY-SA 4.0</a>, <a href="https://commons.wikimedia.org/w/index.php?curid=52379695">Link</a>




___


Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
