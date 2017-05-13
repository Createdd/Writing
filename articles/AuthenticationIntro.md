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
      * [Insert data into MongoDB](#insert-data-into-mongodb)
      * [Hashing and salting](#hashing-and-salting)
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

For the login mask I will use the awesome [template from w3layouts](https://w3layouts.com/register-login-widget-flat-responsive-widget-template/).

Following dependencies will I use
- body-parser (for parsing incoming requests)
- express (to make the application run)
- [nodemon](https://github.com/remy/nodemon) (restarting server when changes occur)
- [mongoose](http://mongoosejs.com/docs/) (object data modeling to simplify interactions with MongoDB)
- [bcrypt](https://www.npmjs.com/package/bcrypt-nodejs) (for hashing and salting passwords)

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
  username: {
    type: String,
    unique: true,
    required: true,
    trim: true
  },
  password: {
    type: String,
    required: true,
  },
  passwordConf: {
    type: String,
    required: true,
  }
});
var User = mongoose.model('User', UserSchema);
module.exports = User;
```

#### Insert data into MongoDB

- add [body-parser](https://github.com/expressjs/body-parser) for parsing incoming request bodies in a middleware
- create a POST route for sending the data to the server
- store the values of the filled out form and store the data in the db with the schema
- it should look like this:

```javascript
if (req.body.email &&
    req.body.username &&
    req.body.password &&
    req.body.passwordConf) {

    var userData = {
      email: req.body.email,
      username: req.body.username,
      password: req.body.password,
      passwordConf: req.body.passwordConf,
    }

    //use schema.create to insert data into the db
    User.create(userData, function (err, user) {
      if (err) {
        return next(err)
      } else {
        return res.redirect('/profile');
      }
    });

```

- use the [mongo shell](https://docs.mongodb.com/manual/reference/mongo-shell/) to see if your data has been saved to the database (it should show a document in `db.users.find()` )

#### Hashing and salting

**Cryptographic** hash functions take a piece of information and return a string, representing this information. Hash values cannot easily be "unhashed" or decrypted and that's why they are a perfect fit for passwords.

**Salt values** are random data that is included with the input for the hash function.

In this tutorial we are using [bcrypt](https://www.npmjs.com/package/bcrypt-nodejs).









<img src="https://images.unsplash.com/photo-1494583882007-bfd2321fb8e2?dpr=2&auto=format&fit=crop&w=1080&h=736&q=80&cs=tinysrgb&crop=&bg=" alt="pic" height="200"/>
https://unsplash.com/photos/qCrocisvGwc

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
