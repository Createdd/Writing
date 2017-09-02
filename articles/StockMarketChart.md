# Charting the Stock Market with React
[<img src="https://images.unsplash.com/photo-1504197618732-93c3d955d927?dpr=2&auto=format&fit=crop&w=1199&h=799&q=80&cs=tinysrgb&crop=">](
https://unsplash.com/photos/a6z2tYFEjR8)
Photo by peggy pardo on Unsplash - https://unsplash.com/photos/a6z2tYFEjR8

Once again I was working on an app from the [FreeCodeCamp curriculum](https://www.freecodecamp.org/challenges/chart-the-stock-market). In this article you can read the full documentation on the building process. 
Enjoy


[➡️ Github Repo is available here ⬅️](https://github.com/DDCreationStudios/ChartTheStockMarket)


## 📄 Table of contents


---
>“Failure isn’t a necessary evil. In fact, it isn’t evil at all. It is a necessary consequence of doing something new.” 
― Ed Catmull
---

## The challenge 

See the full challange [here](https://www.freecodecamp.org/challenges/chart-the-stock-market).

The user stories are pretty simple: 

- I can view a graph displaying the recent trend lines for each added stock.
- I can add new stocks by their symbol name.
- I can remove stocks.
- I can see changes in real-time when any other user adds or removes a stock. For this you will need to use Web Sockets.

It looks like this:

<img src="http://g.recordit.co/RlH1aQ7o9Q.gif" alt="gif"/>

## Roadmap

I learned from [my last full-stack app](https://github.com/DDCreationStudios/Writing/blob/master/articles/LearningsFirstFullStack.md) that starting with the backend can induce some issues when you are working on the frontend later on. Therefore this time I will start with the frontend and finish with the backend.

1. Setup the environment with create-react-app
2. Lay out the basic React component structure
3. Set up the Redux eco system
4. Work over all components, divide them into container components and wire everything up with the Redux store
5. Build the Chart component with React-Vis
6. Build the backend using socket.io
7. Deploy to Heroku

## Frontend

I will only highlight the key cornerstones and not provide a step-by-step tutorial.

#### Setup with the [create-react-app package](https://github.com/facebookincubator/create-react-app)

This time I wanted to use this boilderplate because I have used it many times before but never on a full-stack project. Although it has some limitations with the pre-configured structure, the benefits outweight the problems by a mile. 

Basically it provides an environment, that: 

- React, JSX, ES6, and Flow syntax support.
- Language extras beyond ES6 like the object spread operator.
- A dev server that lints for common errors.
- Import CSS and image files directly from JavaScript.
- Autoprefixed CSS, so you don’t need -webkit or other prefixes.
- A build script to bundle JS, CSS, and images for production, with sourcemaps.
- An offline-first service worker and a web app manifest, meeting all the Progressive Web App criteria.

Pretty early actually I came to the point where I had to eject the configuration ( = opening the environment configuration for changes) to modify the webpack config. 

The problem was that I wanted to add jQuery for Materializecss and there always were some troubles. 
Solutions:
- Import jquery in ES6: https://stackoverflow.com/questions/37213647/es6-code-not-working-with-jquery
- Provide jquery plugin in webpack config: https://github.com/erikras/react-redux-universal-hot-example/issues/596


## Useful links & credits
- [📄 "Begin"](afgafgadgads)



Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->