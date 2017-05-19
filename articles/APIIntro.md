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
  * [Connecting with MongoDB through Mongoose](#connecting-with-mongodb-through-mongoose)
      * [Modeling data for the API](#modeling-data-for-the-api)
      * [Creating the Schema](#creating-the-schema)
      * [Extend the functionality by sorting and voting](#extend-the-functionality-by-sorting-and-voting)
  * [Connecting the API to the database](#connecting-the-api-to-the-database)
      * [Establish error handling](#establish-error-handling)
      * [Update question routes](#update-question-routes)
      * [Update answer routes](#update-answer-routes)
  * [Finalizing and testing the API](#finalizing-and-testing-the-api)
      * [Testing](#testing)
      * [CORS](#cors)
      * [Connecting the Frontend](#connecting-the-frontend)
  * [Conclusion](#conclusion)

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
- catch 404s and pass to custom error handler to send readable JSON messages (if no error is passed, use 500)
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

## Connecting with MongoDB through Mongoose

#### Modeling data for the API

Structure what kind of data has to be stored in a database and what type of relation the data has.
I will use Mongoose to set the data handling for MongoDB. Schemas allow to define the data in JSON format.

In this case this is best implemented using only question objects with answer properties. However, bare in mind, that documents have a storage limit and therefore the amount of answers is limited.

#### Creating the Schema

- create a Schema that follows your desired parent-children structure
- build a model with the Schema
- for example:
```javascript
const AnswerSchema = new Schema({
  text: String,
  createdAt: { type: Date, default: Date.now },
  updatedAt: { type: Date, default: Date.now },
  votes: { type: Number, default: 0 }
});

const QuestionSchema = new Schema({
  text: String,
  createdAt: { type: Date, default: Date.now },
  answers: [AnswerSchema]
});

const Question = mongoose.model('Question', QuestionSchema);
```

#### Extend the functionality by sorting and voting

- answers should be sorted by the newest
- and voting should also be stored in the database
- create a mongoose prehook to sort when saving
- call the child document's parent method to reference the parent document (answer references the question)
- be sure to not use arrow functions when specifying this!
- for example:

```javascript
const sortAnswers = (a, b) => {
  if (a.votes === b.votes) {
    return b.updatedAt - a.updatedAt;
  }
  return b.votes - a.votes;
};
QuestionSchema.pre('save', function (next) {
  this.answers.sort(sortAnswers);
  next();
});

AnswerSchema.method('update', function (updates, callback) {
  Object.assign(this, updates, { updatedAt: new Date() });
  this.parent().save(callback);
});

AnswerSchema.method('vote', function (vote, callback) {
  if (vote === 'up') {
    this.votes += 1;
  } else {
    this.votes -= 1;
  }
  this.parent().save(callback);
});
```

## Connecting the API to the database
___
❗For me this part was the hardest one! Don't worry if you don't get it at the first try right. Make sure to study the mongoose docs properly :)
___

#### Establish error handling

- use the `param` method of the router to trigger callbacks on certain routes (for qID and aID) ([see docs](http://expressjs.com/de/api.html#app.param))
- this way you can always check for errors if the question or answer is not to find
- for example:
```javascript
router.param('qID', (req, res, next, id) => {
  Question.findById(id, (err, doc) => {
    if (err) return next(err);
    if (!doc) {
      err = new Error('Document not found');
      err.status = 404;
      return next(err);
    }
    req.question = doc;
    return next();
  });
});

router.param('aID', (req, res, next, id) => {
  req.answer = req.question.answers.id(id);
  if (!req.answer) {
    err = new Error('Answer not found');
    err.status = 404;
    return next(err);
  }
  return next();
});
```

#### Update question routes

- for the GET route find the questions in your database
- return the questions
- for the POST route (creating new questions) create a new question with the body of the request and save it to the database in JSON format
- for the GET route on one question just response the specific question
- for example:
```javascript
router.get('/', (req, res, next) => {
  Question.find({}).sort({ createdAt: -1 }).exec((err, questions) => {
    if (err) return next(err);
    res.json(questions);
  });
});

router.post('/', (req, res) => {
  const question = new Question(req.body);
  question.save((err, question) => {
    if (err) return next(err);
    res.status(201);
    res.json(question);
  });
});

router.get('/:qID', (req, res) => {
  res.json(req.question);
});
```

#### Update answer routes

- for the POST route (creating answers) simply push the answer to the answer array in the question document and save it with the mongoose methods as JSON
- for the PUT route (updating the answer) return the new JSON with the `update` method
- for the DELETE route (to remove answers) use the `remove` method
- for the POST route (to create voting) use middleware to check for the correct expression and use the `vote` method we defined in the model file
- for example

```javascript
router.post('/:qID/answers', (req, res, next) => {
  req.question.answers.push(req.body);
  req.question.save((err, question) => {
    if (err) return next(err);
    res.status(201);
    res.json(question);
  });
});

router.put('/:qID/answers/:aID', (req, res, next) => {
  req.answer.update(req.body, (err, result) => {
    if (err) return next(err);
    res.json(result);
  });
});

router.delete('/:qID/answers/:aID', (req, res) => {
  req.answer.remove(err => {
    req.question.save((err, question) => {
      if (err) return next(err);
      res.json(question);
    });
  });
});

router.post(
  '/:qID/answers/:aID/vote-:dec',
  (req, res, next) => {
    if (req.params.dec.search(/^(up|down)$/) === -1) {
      const err = new Error(`Not possible to vot for ${req.params.dec}!`);
      err.status = 404;
      next(err);
    } else {
      req.vote = req.params.dec;
      next();
    }
  },
  (req, res, next) => {
    req.answer.vote(req.vote, (err, question) => {
      if (err) return next(err);
      res.json(question);
    });
  }
);
```

___
At this point the REST API is completely implemented and ready to be consumed.
___

Check out a timelapse of my implementation: (click on the picture ;) )
[![Youtube video](https://i.ytimg.com/vi_webp/KVHmi9vq-FU/maxresdefault.webp)](https://www.youtube.com/watch?v=KVHmi9vq-FU)

## Finalizing and testing the API

#### Testing

To test whether all routes are doing what they should I'll use the chrome extension of [Postman](https://www.getpostman.com/). The interface allows to test all HTTP methods efficiently.

On a note: Instead of testing all routes manually automated tests can also be set up. ;)

#### CORS

Cross Origin Resource Sharing allows the browser though headers to access resources from a different domain. Due to security risk this is restricted.

Check out [this article](https://www.html5rocks.com/en/tutorials/cors/) for an introduction to CORS.

We have to build a middleware that allows domains to consume the API

- set the header to allow access to all origins
- allow HTTP methods
- for example:
```javascript
app.use((req, res, next) => {
  res.header('Access-Control-Allow-Origin', '*');
  res.header(
    'Access-Control-Allow-Headers',
    'Origin, X-Requested-With, Content-Type, Accept'
  );
  if (req.method === 'Options') {
    res.header('Access-Control-Allow-Methods', 'PUT, POST, DELETE');
    return res.status(200).json({});
  }
});
```

<img src="https://images.unsplash.com/photo-1428605821565-9ffceeb3dc9a?dpr=2&auto=format&fit=crop&w=1080&h=720&q=80&cs=tinysrgb&crop=&bg=" alt="pic" height="200"/>
https://unsplash.com/photos/PJCZOWuOxbU

#### Connecting the Frontend

The working API can be connected to all types of frontend frameworks. Maybe I'll do that and write another article. :)

## Conclusion

As we can see a REST API is a great tool for setting up basic backend microservices. For actually implementing the API it is necessary to fully understand the database you are working with and it's interaction with routes. In this case this was mongoose.

Also keep in mind, that for production you will certainly need User Authentication and Authorization to manage identity and access rights.


If you gained something from this article let me know with a comment or heart. Make sure to follow for more :)


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
