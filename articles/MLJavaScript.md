# Basic JavaScript AI Algorithm
[<img src="https://images.unsplash.com/photo-1500835176302-48dbd01f6437?dpr=2&auto=format&fit=crop&w=1080&h=784&q=80&cs=tinysrgb&crop=">](
https://unsplash.com/photos/7FNOH-qSxMI)
Photo by Tom Barrett on Unsplash


[➡️ Github Repo is available here ⬅️](https://github.com/DDCreationStudios/RESTAPIIntro)

AI and machine learning was number 1 on my list when I started to code. Now I am facing the problem that there are so many resources to dive into the topic. My goal is clear: I want to implement the basics of machine learning with JavaScript - so I did.


## 📄 Table of contents


---
>“Human beings, viewed as behaving systems, are quite simple. The apparent complexity of our behavior over time is largely a reflection of the complexity of the environment in which we find ourselves.” 
― Herbert A. Simon, The Sciences of the Artificial
---

## Resources

In this article I am simply going to build something similiar to that from [Burak Kanber's article "Machine Learning: Introduction to Genetic Algorithms"](http://burakkanber.com/blog/machine-learning-genetic-algorithms-part-1-javascript/)

In his article he not only explains fundamentals very well but also uses his knowledge in a JavaScript example. 
I was very enlighted and amazed. 
Visit [his homepage](https://www.burakkanber.com/) for more great stuff. :) 

## What we are building

We are programing an algorithm in Javascript that reproduces the word "JavaScript".

This is an example for understanding basic concepts. It is very basic and even contrived, since the algorithm itself contains the desired outcome (the typed word).

## The reducing possible outcome

There are many possible outcomes for building the desired string. Assuming a certain length for the solution, like 10 characters long, will reduce the amount of candidates. 

For example:
```
- JavsScrip!
- Javahztrew
- WerdScript
- JavaScript
```

These would all be possible candidates for a solution regarding their length, but obviously only the last one is correct. 

## Cost function

A [cost function](https://en.wikipedia.org/wiki/Loss_function) helps us to minimize the cost (the difference to the desired outcome). 

![img](https://wikimedia.org/api/rest_v1/media/math/render/svg/cf4beff1dc104f16784ac54e594efbdaa72480b6)

Quoting the article: 
>For each character in the string, figure out the difference in ASCII representation between the candidate character and the target character, and then square it so that the "cost" is always positive.

>For example, if we have a capital "A" (ASCII 65) but it's supposed to be a capital "C" (ASCII 67), then our cost for that character is 4 (67 - 65 = 2, and 2^2 = 4).

To get to our desired goal to reproduce the string we are aiming for a cost of 0.

In this basic example it is safe to assume that the algorithm can be stopped after it had reached the cost of 0. Be aware that other, more complex problems might need to run a certain time and evaluate their own minimized result.

## Comparing results

Next we need to combine and compare the results.

For example:

```
- SavaScript
- JavaScripd
```

can be cut in half and afterwards combining one string with the other like:

```
- SavaScripd
- JavaScript
```

The result now shows one correct string and one that is not.

## Changing candidates

In order to avoid in-breeding we need to alter the candidates after combining.

For example:
```
- JadaScript
- JadaScript
```

This situation will never yield improving results, since they are the candidates are exactely the same. 

We need to alter at least one of them a little to evolve. 
For example "JaeaScript" would fit well to continue a successful evolution.

## Summarizing the candidates

Thinking it object oriented programming we can lay out the following:

We have a candidate class with 

- the string
- cost score 

as property and 

- combining
- altering
- calculating the cost score

as methods.

## Build a group

We will choose a population size and evolve the candidates inside.
The group has to experience different stages. In those stages we need to
- calculate the cost score for each candidate
- sort the candidates by the score
- removing unfit candidates
- altering the best candidates
- altering candidates randomly
- a completness test to check if the correct string is found








## Useful links & credits
- [📄 "Begin"](afgafgadgads)



Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
