# Coffee and Code - A dosing strategy

[<img src="https://images.unsplash.com/photo-1422207049116-cfaf69531072?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=85a9d93b9441617bb2fce231a81de8c0&auto=format&fit=crop&w=2220&q=80">](
https://unsplash.com/photos/VxtWBOQjGdI)
Photo by Stephen Leonardi on Unsplash - https://unsplash.com/photos/VxtWBOQjGdI

I consider myself a productive person. Of course I like to drink caffeinated beverages to maximize my outcome. Recently I came across this article and thought it might be worth sharing my thoughts on it.

This article relies heavily on [this research paper](https://onlinelibrary.wiley.com/doi/epdf/10.1111/jsr.12711) and my personal experiences.

## Table of Contents

<!-- TOC -->

- [Coffee and Code - A dosing strategy](#coffee-and-code---a-dosing-strategy)
  - [Table of Contents](#table-of-contents)
  - [Using an optimization algorithm?](#using-an-optimization-algorithm)
  - [](#)

<!-- /TOC -->

## Using an optimization algorithm?

I refer to the [research paper on "Caffeine dosing strategies to optimize alertness during sleeploss"](https://onlinelibrary.wiley.com/doi/epdf/10.1111/jsr.12711) by Francisco G. Vital-Lopez, Sridhar Ramakrishnan, Tracy J. Doty, Thomas J. Balkin and Jaques Reifman. 

As they put it in the summary: 
> In this work, we provide an optimization algorithm, suited for mobile computing platforms, to determine when and how much caffeine to consume, so as to safely maximize neurobehavioural performance at the desired time of the day, under any sleep-loss condition

I assume that many ambitious people have once in their lifetime suffered from a form of sleep loss and therefore this findings can help to improve the use of caffeine. I most certainly was curious.

Since standard algorithms were not able to solve the optimization problem in a reasonable computational time they looked for an approximate solution using the tabu search algorithm.

The goal was a twofold optimization:
1. enhancing neurobehavioural performance and 
1. reducing caffeine consumption

Although the were able to come up with an algorithm, there were some problems to consider:
> However, there may be considerable individual variability in both the response to sleep loss and the restorative effects of caffeine. Variation in the effect of caffeine is, in part, a result of genetic polymorphisms in the genes coding for the main caffeine-metabolizing enzyme, P-450, and the main caffeine targets, adenosine receptors A1and A2A. To assess how well a group-average model captures individual differences, we computed the root mean squared error (RMSE) between the model predictions and the measured mean RT data from each subject after caffeine consumption.

And resulted in: 

> This result suggests that a group-average model cannot always be used to obtain optimal caffeine strategies at the individual level

Nevertheless, I like the idea very much. The combination of a validated mathematical model with optimization methods to determine when and how much caffeine to consume to achieve peak performance at the most needed times is very interesting.

They plan to add the algorithm to [this page](https://2b-alert-web.bhsai.org/2b-alert-web/login.xhtml) and make it useable for the public. 

Looking forward to that!

## 

 



---

Thanks for reading my article! Feel free to leave any feedback! 

---

Daniel is a LL.M. student in business law, working as a software engineer and organizer of tech related events in Vienna. 
His current personal learning efforts focus on machine learning. 

Connect on:
- [LinkedIn](https://www.linkedin.com/in/createdd) 
- [Github](https://github.com/Createdd)
- [Medium](https://medium.com/@ddcreationstudi)
- [Twitter](https://twitter.com/DDCreationStudi)
- [Steemit](https://steemit.com/@createdd)
- [Hashnode](https://hashnode.com/@DDCreationStudio)

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->