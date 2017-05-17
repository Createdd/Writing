# Starting with Authentication

[<img src="https://images.unsplash.com/photo-1468817814611-b7edf94b5d60?dpr=2&auto=format&fit=crop&w=1080&h=1620&q=80&cs=tinysrgb&crop=&bg=">](
https://unsplash.com/photos/th3rQu0K3aM)
https://unsplash.com/photos/th3rQu0K3aM




## 📄 Table of contents


<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [Starting with Authentication](#starting-with-authentication)
  * [📄 Table of contents](#table-of-contents)
  * [REST API?](#rest-api)
  * [What I will use for this introduction](#what-i-will-use-for-this-introduction)
      * [Development Environment](#development-environment)
      * [Dependencies](#dependencies)
      * [Structure](#structure)
  * [Building the API routes](#building-the-api-routes)
      * [Set up basics](#set-up-basics)
      * [Create question routes](#create-question-routes)
      * [Create answer routes](#create-answer-routes)
      * [Set up error handlers](#set-up-error-handlers)
  * [Modeling data for the API](#modeling-data-for-the-api)
  * [Communicating with Mongo through Mongoose](#communicating-with-mongo-through-mongoose)
  * [Finalizing and testing the API](#finalizing-and-testing-the-api)
  * [Conclusion](#conclusion)
  * [Useful links & credits](#useful-links-credits)

<!-- tocstop -->



---
>"We see our customers as invited guests to a party, and we are the hosts. It's our job every day to make every important aspect of the customer experience a little bit better."  - Jeff Bezos
---

## REST API?

REST APIs handle the server side of the web application. That means that the backend is built once and can provide content or data for frontend, mobile, or other server-side apps.
A great example is the [google calendar API](https://developers.google.com/google-apps/calendar/v3/reference/).

REST stands for Representational State Transfer and is a way how a web server should respond to requests. This allows to not only read data, but also do different things like updating, deleting or creating data.

I'm going to build an application that allows to ask questions to the stackoverflow API.
Therefore we need to be able to:
- ask, read, answer questions
- read, edit, delete answers
- voting on answers



## What I will use for this introduction

#### Development Environment

In this example here I will use

Plain JavaScript
- Node.js
- Express (JS framework)
- MongoDB (Database)
- Yarn (package management)
- Visual Studio Code as editor
- [Postman](https://www.getpostman.com/) (testing APIs)

For the login mask I will use the awesome template from w3layouts.

#### Dependencies

Following packages are used

- body-parser (for parsing incoming requests)
- express (to make the application run)
- [nodemon](https://github.com/remy/nodemon) (restarting server when changes occur)
- [mongoose](http://mongoosejs.com/docs/) (object data modeling to simplify interactions with MongoDB)
- [morgan](https://www.npmjs.com/package/morgan) (HTTP request logger middleware )

#### Structure

For programming the API it is key to structure the routes properly. We will set url

The tutorial will be structured in:

- building the API routes with express
- modeling data for the API
- communicating with Mongo through Mongoose
- finalizing and testing the API


## Building the API routes

#### Set up basics
- install the nodemon package to simplify developing and add the script in the package.json accordingly
- start with creating a basic web server in an express app (check out the docs of express for an example)
- use express middleware to be as flexible as possible
- add the body-parser package to parse requests
- use the parser in a middleware

#### Create question routes

- create a router.js file to store all routes
- set up GET and POST routes to look at questions and create them
- set up a GET route for specific questions
- for example:
```javascript
router.get('/', (req, res) => {
  res.json({ response: 'a GET request for LOOKING at questions' });
});

router.post('/', (req, res) => {
  res.json({
    response: 'a POST request for CREATING questions',
    body: req.body
  });
});

router.get('/:qID', (req, res) => {
  res.json({
    response: `a GET request for LOOKING at a special answer id: ${req.params.qID}`
  });
});
```

#### Create answer routes
- install the morgan package for logging http requests (helps analyzing your requests in the console)
- set up the POST route for creating answers
- set up the PUT and DELETE route for editing and deleting answers
- set up a POST route for creating voting on answers
- for example:

```javascript
router.post('/:qID/answers', (req, res) => {
  res.json({
    response: 'a POST request for CREATING answers',
    question: req.params.qID,
    body: req.body
  });
});

router.put('/:qID/answers/:aID', (req, res) => {
  res.json({
    response: 'a PUT request for EDITING answers',
    question: req.params.qID,
    answer: req.params.aID,
    body: req.body
  });
});

router.delete('/:qID/answers/:aID', (req, res) => {
  res.json({
    response: 'a DELETE request for DELETING answers',
    question: req.params.qID,
    answer: req.params.aID,
    body: req.body
  });
});

router.post('/:qID/answers/:aID/vote-:dec', (req, res) => {
  res.json({
    response: 'a POST request for VOTING on answers',
    question: req.params.qID,
    answer: req.params.aID,
    vote: req.params.dec,
    body: req.body
  });
});
```

#### Set up error handlers

- use middleware to catch errors efficiently
- catch 404s and pass to custom error handler (if no error is passed use 500)
- create an individual validation middleware for voting errors (only allowing up or down voting)
- for example:

```javascript
app.use((req, res, next) => {
  const err = new Error('Not Found');
  err.status = 404;
  next(err);
});
app.use((err, req, res, next) => {
  res.status(err.status || 500);
  res.json({
    error: {
      message: err.message
    }
  });
});
```

## Modeling data for the API


## Communicating with Mongo through Mongoose


## Finalizing and testing the API


<img src="https://images.unsplash.com/photo-1428605821565-9ffceeb3dc9a?dpr=2&auto=format&fit=crop&w=1080&h=720&q=80&cs=tinysrgb&crop=&bg=" alt="pic" height="200"/>
https://unsplash.com/photos/PJCZOWuOxbU

## Conclusion



## Useful links & credits
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
-

```
If you gained something from this article let me know with a comment or heart. Make sure to follow for more :)
```

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
