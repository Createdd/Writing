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

Thinking in object oriented programming we can lay out the following:

We have a candidate class with 

- the string
- cost score 

as property and 

- combining
- altering
- calculating the cost score

as methods.

## Building a group

We will choose a population size and evolve the candidates inside.
The group has to experience different stages. In those stages we need to
- calculate the cost score for each candidate
- sort the candidates by the score
- removing unfit candidates
- altering the best candidates
- altering candidates randomly
- a completness test to check if the correct string is found

## Code

First we set a class with a string as constructor and set a method for building a random string:

```javascript
var Candidates = function(code) {
    if (code) this.code = code;
    this.cost = 9999;
};
Candidates.prototype.code = '';
Candidates.prototype.random = function(length) {
    while (length--) {
        this.code += String.fromCharCode(Math.floor(Math.random() * 255));
    }
};
```

Next we need to add the cost function, which finds the differences between the ASCII code and squares them.

```javascript
Candidates.prototype.calcCost = function(compareTo) {
	var total = 0;
	for (i = 0; i < this.code.length; i++) {
		total +=
			(this.code.charCodeAt(i) - compareTo.charCodeAt(i)) *
			(this.code.charCodeAt(i) - compareTo.charCodeAt(i));
	}
	this.cost = total;
};
```

After that we build the combine function, which takes a candidate as an argument, finds the middle and returns an array of two new children.

```javascript
Candidates.prototype.combine = function(cand) {
	var pivot = Math.round(this.code.length / 2) - 1;

	var child1 = this.code.substr(0, pivot) + cand.code.substr(pivot);
	var child2 = cand.code.substr(0, pivot) + this.code.substr(pivot);

	return [new Candidates(child1), new Candidates(child2)];
};
```

Next we need to alter a chracter from the string. Therefore we pick a random position in the string and randomly increase the character by 1 or -1. Afterwards we replace the old string with the new string.


```javascript
Candidates.prototype.mutate = function(chance) {
	if (Math.random() > chance) return;

	var index = Math.floor(Math.random() * this.code.length);
	var upOrDown = Math.random() <= 0.5 ? -1 : 1;
	var newChar = String.fromCharCode(this.code.charCodeAt(index) + upOrDown);
	var newString = '';
	for (i = 0; i < this.code.length; i++) {
		if (i == index) newString += newChar;
		else newString += this.code[i];
	}

	this.code = newString;
};
```

Next we need to build a group of candidates. The class constractor takes the target string and the size of the group as arguments and fills it with random candidates.

```javascript
var Group = function(goal, size) {
	this.members = [];
	this.goal = goal;
	this.stageNumber = 0;
	while (size--) {
		var gene = new Candidates();
		gene.random(this.goal.length);
		this.members.push(gene);
	}
};
```
After that we need to sort the Candidates by their cost score.

```javascript
Group.prototype.sort = function() {
	this.members.sort(function(a, b) {
		return a.cost - b.cost;
	});
};
```

Then we need to write a simple display function to actually build some HTML on the page. Basically we want to display the stage we are in and all the current candidates of the group.

```javascript
Group.prototype.display = function() {
	document.body.innerHTML = '';
	document.body.innerHTML += '<h2>Stage: ' + this.stageNumber + '</h2>';
	document.body.innerHTML += '<ul>';
	for (var i = 0; i < this.members.length; i++) {
		document.body.innerHTML +=
			'<li>' + this.members[i].code + ' (' + this.members[i].cost + ')';
	}
	document.body.innerHTML += '</ul>';
};
```

The next step is to actually create a stage. Therefore we calculate the costs, sort the candidates, display the result, combine the best results and mutate the result. Then repeat the cycle. We set the break with an if-statement when the string of member equals our goal.


```javascript
Group.prototype.stage = function() {
	for (var i = 0; i < this.members.length; i++) {
		this.members[i].calcCost(this.goal);
	}

	this.sort();
	this.display();
	var children = this.members[0].combine(this.members[1]);
	this.members.splice(this.members.length - 2, 2, children[0], children[1]);

	for (var i = 0; i < this.members.length; i++) {
		this.members[i].mutate(0.5);
		this.members[i].calcCost(this.goal);
		if (this.members[i].code == this.goal) {
			this.sort();
			this.display();
			return true;
		}
	}
	this.stageNumber++;
	var scope = this;
	setTimeout(function() {
		scope.stage();
	}, 20);
};
```

```javascript

```







## Useful links & credits
- [📄 "Begin"](afgafgadgads)



Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
