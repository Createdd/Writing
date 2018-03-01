# Machine Learning Basics - Part 3 - Vector Machines, Unsupervised Learning and Principal Component Analysis

[<img src="https://images.unsplash.com/photo-1519834089823-08a494ba5a12?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=f514c48e4c073296bec3c7f587955ab1&auto=format&fit=crop&w=1936&q=80">](
https://unsplash.com/photos/vR-Nb0bncOY)
Photo by Fahrul Azmi on Unsplash - https://unsplash.com/photos/vR-Nb0bncOY

In this article I revisit the learned material from the amazing [machine learning course by Andre Ng on Coursera](https://www.coursera.org/learn/machine-learning) and create an overview about the concepts. The article is not designed as a tutorial but rather to fresh up on the basic ideas.

All quotes refer to the material from the course if not explicitly stated otherwise.

## Table of Contents
<!-- TOC -->

- [Machine Learning Basics - Part 3 - Vector Machines, Unsupervised Learning and Principal Component Analysis](#machine-learning-basics---part-3---vector-machines-unsupervised-learning-and-principal-component-analysis)
  - [Table of Contents](#table-of-contents)
  - [Anomaly detection](#anomaly-detection)

<!-- /TOC -->

## Anomaly detection

Anomaly detection tests a new example against the behavior of other examples in that range. This idea is often used in fraud detection, manufacturing or monitoring of machines. It is always useful if the goal is to detect certain outliners.

Using a Gaussian distribution algorithm implies that the example x is distributed with a mean mu and variance sigma squared.

The formula for mu and sigma squared are:

![muSigmaAD](../assets/mlIntro/muSigmaAD.png)

The formula for calculating the probability is:

![probAD](../assets/mlIntro/probAD.png)




---
 
This wraps up the third part. In the next one, anomaly detection, recommender systems and scaling issues will be described. Stay tuned!

---

Thanks for reading my article! Feel free to leave any feedback! 

---

Daniel is a LL.M. student in business law, working as a software engineer and organizer of tech-related events in Vienna. 
His current personal learning efforts focus on machine learning. 

Connect on:
- [LinkedIn](https://www.linkedin.com/in/createdd) 
- [Github](https://github.com/DDCreationStudios)
- [Medium](https://medium.com/@ddcreationstudi)
- [Twitter](https://twitter.com/DDCreationStudi)
- [Steemit](https://steemit.com/@createdd)
- [Hashnode](https://hashnode.com/@DDCreationStudio)
