# Starting with Authentication (A tutorial with Node.js and MongoDB)

[<img src="https://images.unsplash.com/photo-1463136729667-22694f9bbc52?dpr=2&auto=format&fit=crop&w=1080&h=720&q=80&cs=tinysrgb&crop=&bg=">](
https://unsplash.com/photos/tGbugCIBaCo)
https://unsplash.com/photos/tGbugCIBaCo

Authentication is an important issue when creating a dynamic web application. This article should clear things up and provide a basic instruction.


## 📄 Table of contents


<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [Starting with Authentication (A tutorial with Node.js and MongoDB)](#starting-with-authentication-a-tutorial-with-nodejs-and-mongodb)
  * [📄 Table of contents](#table-of-contents)
  * [Authentication?](#authentication)
  * [What I will use for this introduction](#what-i-will-use-for-this-introduction)
  * [User registration](#user-registration)
      * [Connect to MongoDB](#connect-to-mongodb)
      * [Create a schema](#create-a-schema)
  * [Conclusion](#conclusion)
  * [Useful links & credits](#useful-links-credits)

<!-- tocstop -->



---

>"For me, privacy and security are really important. We think about it in terms of both: You can't have privacy without security." - Larry Page

---

## Authentication?

Authentication is for identifying users and provide different access rights and content depending on their id.
In most cases the application provides a login form with certain credentials to verify a user.

It's necessary to understand:
- authentication as
- authorization as
- a session
- cookies


## What I will use for this introduction

In this example here I will use
- Plain JavaScript
- Node.js
- Express (JS framework)
- MongoDB (Database)
- Yarn (package management)
- Visual Studio Code as editor

for writing the authentication.

For the login mask I will use the awesome [template from w3layouts](https://w3layouts.com/proficient-login-form-flat-responsive-widget-template/).

Following dependencies will I use
- body-parser (for parsing incoming requests)
- express (to make the application run)
- [nodemon](https://github.com/remy/nodemon) (restarting server when changes occur)
- [mongoose](http://mongoosejs.com/docs/) (object data modeling to simplify interactions with MongoDB)

The tutorial will be structured in:
- User registration (setting up routes and database)
- Sessions and Cookies (connecting them to login routes)
- Creating custom middleware (to improve the performance)

## User registration

I'll start with a basic express starter setup, which simply creates a webserver and serves the static files from the template on the home route. [(see on Github commit)](https://github.com/DDCSLearning/authenticationIntro/commit/97da94b5b6b52c4f2452d92eb0e92a110a97a1f4)

#### Connect to MongoDB

- install [Mongoose](http://mongoosejs.com/docs/)
- install mondodb
- setup up mongod if you haven't [(tutorial)](https://treehouse.github.io/installation-guides/mac/mongo-mac.html)
- be sure to start nodemon again with the running mongod on localhost!

#### Create a schema

MongoDB is a document database, which stores JSON like objects. The model/schema describes what this objects should contain.

- create a schema according to the [docs](http://mongoosejs.com/docs/guide.html) and store it in an own folder
- the schema should describe the fields we have in our form and specify the data it can expect

It should look something like this:

```javascript
var mongoose = require('mongoose');
var UserSchema = new mongoose.Schema({
  email: {
    type: String,
    unique: true,
    required: true,
    trim: true
  },
  password: {
    type: String,
    required: true,
  }
});
var User = mongoose.model('User', UserSchema);
module.exports = User;
```












<img src="https://images.unsplash.com/photo-1475650522725-015d35677789?dpr=2&auto=format&fit=crop&w=767&h=511&q=80&cs=tinysrgb&crop=&bg=" alt="pic" height="200"/>
https://unsplash.com/photos/OCrPJce6GPk

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
