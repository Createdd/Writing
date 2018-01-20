# The concept of regression - use the power in everyday life

[<img src="https://images.unsplash.com/photo-1504333638930-c8787321eee0?auto=format&fit=crop&w=1500&q=80">](
https://unsplash.com/photos/f7YQo-eYHdM)
Photo by Bryan Goff on Unsplash - https://unsplash.com/photos/f7YQo-eYHdM


## 📄 Table of contents


---
>"By their very nature, heuristic shortcuts will produce biases, and that is true for both humans and artificial intelligence, but the heuristics of AI are not necessarily the human ones." - Daniel Kahneman
---

## What Regression analysis is all about 

The Regression analysis is a statistical method evaluating the relationship between different variables. 

This can be a very powerful tool in decision making. If you think certain variables in your everyday life, for example profits and sales, have a relationship, this method helps evaluate your assumptions and provide additional information for future actions. The benefits apply to as well for business men of highest rank deciding future plans in their businesses but also for ordinary people trying to improve their day-to-day decisions.

# How to apply this concept

### Find variables

For simplicity reasons I want to explain the simple linear regression concept, because it is already effective and easy to apply.

In this case we need to find a one(!) variable, which is dependent on another variable. An easy example would be sales and profit. 
The Profit variable is directly dependent on the sales variable. 

An important factor is linearity, which means that the factor follows the linear equation.

As wikipedia defines it: 
>"A linear equation is an algebraic equation in which each term is either a constant or the product of a constant and (the first power of) a single variable (however, different variables may occur in different terms)."

Or simple: When scatter plotted on a graph, the relationship can be illustrated on a straight line.

[![gif](https://camo.githubusercontent.com/8702cf6f8016bc06f20490036fa028e065cf38cf/687474703a2f2f672e7265636f726469742e636f2f647271577035393139352e676966)](https://ddcreationstudios.github.io/logisticRegression/)

### Create and test the model

The most common technique to for evaluating the model is called "ordinary least squares". 

Basically, the formula tries to use the slope and the intercept of the regression equation to measure the relationship between the 2 variables and minimize the distance from further dependent variables.

Test the model with a null hypothesis measuring if there is a relationship between the variables. If the null hypothesis equals zero and can't be rejected, there is no relationship between variables. 

Each estimated coefficient in a regression equation must be tested to determine if it is statistically significant. If a coefficient is statistically significant, the corresponding variable helps explain the value of the dependent variable (Y). (The null hypothesis tests the coefficient being zero.)

This other hypothesis test can be conducted with a p-value (probability value).
The p-value is compared to the level of significance for the hypothesis test and if the p-value is less than the level of significance the variable is statistically significant. (the null hypothesis that tests the coefficient equals zero is rejected!)



## Math behind the model

Testing the accuracy of the null hypothesis can be done with the "cost function".

![cost function](../assets/ConceptRegression/costFunction.png)

This function compares the average of the predicted and real values.
The goal is to choose the parameters so that the difference of the null hypothesis of x to the actual y is as small as possible.






## Useful links & credits
- [📄 "Begin"](afgafgadgads)

---

Thanks for reading my article! Feel free to leave any feedback! 

---

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
