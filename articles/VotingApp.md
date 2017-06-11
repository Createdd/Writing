# Building the Free Code Camp Voting App

[<img src="https://images.unsplash.com/photo-1495316364083-b5916626072e?dpr=2&auto=format&fit=crop&w=1080&h=720&q=80&cs=tinysrgb&crop=&bg=">](
https://unsplash.com/photos/OwMTchwUTNw)
https://unsplash.com/photos/OwMTchwUTNw

The Voting App on Free Code Camp is in my opinion the first challenge, that was really hard. I just couldn't do it as easy as all the other challenges. Too much knowledge in too much fields is required. Also, I didn't find any tutorials or examples, that broke this challenge down with up-to-date tools. So I decided to document it my building process.

I will use:
- MongoDB
- Express
- React + Redux
- Node.js

also known as "MERN-Stack".

Have fun :)

[➡️ Github Repo is available here ⬅️](https://github.com/DDCreationStudios/https://github.com/DDCreationStudios/votingApp)

If you like to follow this article in depth, make sure to read it also on github [here](https://github.com/DDCreationStudios/Writing/blob/master/articles/VotingApp.md). (Since Github provides more specific styling possibilities)


## 📄 Table of contents


<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [Building the Free Code Camp Voting App](#building-the-free-code-camp-voting-app)
  * [📄 Table of contents](#table-of-contents)
  * [What this article is about](#what-this-article-is-about)
      * [Structure](#structure)
      * [Development Environment](#development-environment)
      * [Packages / Features / Dependencies](#packages-features-dependencies)
  * [First things first](#first-things-first)
  * [Backend](#backend)
      * [Set up Packages, Middleware and Mongoose](#set-up-packages-middleware-and-mongoose)
      * [Set up your routes](#set-up-your-routes)
      * [Set up Mongoose and your Schemas and connect everything to your routes](#set-up-mongoose-and-your-schemas-and-connect-everything-to-your-routes)
      * [Establish authentication and authorization with Twitter](#establish-authentication-and-authorization-with-twitter)
      * [Establish local authentication and authorization](#establish-local-authentication-and-authorization)
  * [Frontend](#frontend)
      * [Think before you do!](#think-before-you-do)
      * [Necessary setup with Babel and Webpack](#necessary-setup-with-babel-and-webpack)
      * [Structure components](#structure-components)
      * [Design and build components](#design-and-build-components)
      * [Connect React to the Express Backend with React Router](#connect-react-to-the-express-backend-with-react-router)
  * [Visualization](#visualization)
  * [Deployment / DevOps](#deployment-devops)
      * [Docker](#docker)
  * [Useful links & credits](#useful-links-credits)

<!-- tocstop -->




---
>"I fear not the man who has practiced 10 000 kicks once, but I fear the man who has practiced one kick 10 000 times."  - Bruce Lee
---

## What this article is about

In this article I will describe the process of building the Voting App for the [Free Code Camp Challenge](https://www.freecodecamp.com/challenges/build-a-voting-app).
For beginners: Be sure to read the documentation of each tool you use properly. There is no shortcut to success. Try, fail and learn. ;)
For everybody: This is no optimized example for building the application. I am open for feedback of any kind. I am still a beginner :)

___
Always read the documentation to each tool you use!
___


#### Structure

To break down this application I will divide it into sections for backend, frontend, data visualization and the deployment process. The project will be available as open source code on Github, where you can follow up with commits and the end result.


#### Development Environment

- Plain JavaScript
- Node.js
- Express (JS framework)
- MongoDB (Database)
- Yarn (package management)
- Visual Studio Code as editor
- [Postman](https://www.getpostman.com/) (testing APIs)


#### Packages / Features / Dependencies

General
- ([ES 6](http://es6-features.org/) (JS scripting-language specification))
- [eslint](https://www.npmjs.com/package/eslint) with Airbnb extension (for writing higher quality code)
- [nodemon](https://github.com/remy/nodemon) (restarting server when changes occur)
- [Babel](https://babeljs.io/) (javascript compiler)
- [Webpack](https://webpack.github.io/) (module bundler/builder)
- [dotenv](https://www.npmjs.com/package/dotenv) (for configuring environment variables)


Backend
- [Node.js](https://nodejs.org/) (JS runtime environment for server-side)
- [MongoDB](https://www.mongodb.com/what-is-mongodb) (document based database)


- [body-parser](https://github.com/expressjs/body-parser) (for parsing incoming requests)
- [express](http://expressjs.com/de/) (to make the application run)
- [mongoose](http://mongoosejs.com/docs/) (object data modeling to simplify interactions with MongoDB)
- [morgan](https://www.npmjs.com/package/morgan) (HTTP request logger middleware)

Frontend
- [React]() (JS framework)
- [Redux]() (state management for React)
- [Materialize CSS](http://materializecss.com/) (framework for material design)



Visualization

- react vis?
- deck gl?
- D3?
- google charts?

Deployment / DevOps

- [Heroku](https://www.heroku.com/) (PaaS to run applications in the cloud) ?
- AWS?
- CI Travis
- Terraform?

(Unit)Testing

- Not implemented in this app (but normally it should)
- Manual testing as long as feasible

## First things first

First I will set up my environment:
- add git for version control
- create your package management with yarn init
- add express for a fast web development
- add the nodemon package for restarting your server on changes
- add eslint.rc for your eslint configuration
- add babel and corresponding plugins for compiling JS


As additional integration I'll use:
- Travis CI (for contineous integration)
- Code Climate (for Code quality)
- Assertible (Monitoring Web Services, especially checking deployment  - Quality Assurance)

[Check out my commit on Github after the setup.](https://github.com/DDCreationStudios/votingApp/tree/23a05a550f6e2e34cb182d3a271a4c44028d07f9)

## Backend

I will start with the backend, since it's the most difficult in my opinion.

#### Set up Packages, Middleware and Mongoose

I will use:
- [body-parser](https://github.com/expressjs/body-parser) for parsing request bodies
- [morgan](https://www.npmjs.com/package/morgan) for logging out HTTP requests
- [compression](https://www.npmjs.com/package/compression) for compressing response bodies
- [helmet](https://www.npmjs.com/package/helmet) for setting basic security with HTTP headers
- [mongoose](https://www.npmjs.com/package/mongoose) object modeling tool for asynchronous database connection


Next
- create a constants file to set you different environment variables and corresponding settings
- create a middleware file to pass in middleware to your app and differentiate for environments (especially use bodyparser and morgan packages here)
- create a database file to set up the mongoDB connection
- modularize your code and outsource your constants, middleware and database connection for keeping smaller files
- don't forget to import everything in your app.js file, pass in the middleware function and test your setup with a simple http request

[Check out my commit on Github after the setup.](https://github.com/DDCreationStudios/votingApp/tree/88a2436697be4147302ce2dbcd3104ed564c86fe)

#### Set up your routes

Revisit  the User stories and lay out your routes accordingly

Following the [CRUD principle:](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete)

As an unauthenticated user I want to
- see all polls (R)
- see individual polls (R)
- vote on available polls (C)

As an authenticated user I want to
- see/read all polls (R)
- see individual polls (R)
- vote on available polls (C)
- create new polls (C)
- create new options/votes (C)
- delete polls (D)

Therefore:
- set up [error handling as middleware](http://expressjs.com/en/guide/error-handling.html)
- set up your [router object](http://expressjs.com/en/4x/api.html#router)
- create your GET, POST, DELETE routes and response with json objects
- test the set up routes with postman (all should have a status code of 200)
- connect your routes to your middleware and app.js

#### Set up Mongoose and your Schemas and connect everything to your routes

When setting up Schemas think about how you want to structure you documents that have to be stored in the database. In this example we need to store user for the authentication process and polls with answers.

For polls we need:
- the question
- answers/votes

- create your mongoose schemas and models
- connect to [mlab](https://mlab.com/) to monitor your DB actions better
___
Be aware that mlab creates those "System Collections" that throw "duplicate key error index dup key: { : null }" error in postman, when creating new polls. Till now I didn't find a solution but deleting all collections allows to start again. ;)
___
- use the dotenv package to store your credentials in the environment and add the .env file to .gitignore (if you make your project open source)
- connect you routes with your mongoose model to handle the documents in MongoDB


> BE SURE TO READ THE [DOCS](http://mongoosejs.com/docs/models.html) when you are stuck. This part is pretty hard when you haven't done a lot with mongoose and MongoDB!

[Check out my commit on Github after these steps.](https://github.com/DDCreationStudios/votingApp/tree/5dcd7359d2cb1b31e28a08869461b927094550c0)

#### Establish authentication and authorization with Twitter

I want to use the twitter sign-on as an [OAuth](https://oauth.net/) provider to authenticate. It provides better user experience and I also got to explore OAuth.

>OAuth is a standard protocol that allows users to authorize API access to web and desktop or mobile applications. Once access has been granted, the authorized application can utilize the API on behalf of the user.


Of course I found [the great article](https://scotch.io/tutorials/easy-node-authentication-twitter) on how to set up the authentication process in Nodejs. After failing to implement it properly in my app (took me a whole day) I decided to dive straight into the [documentation of passport](http://passportjs.org/docs)!

I love the quote the put up there:

>Despite the complexities involved in authentication, code does not have to be complicated.

___
⭐ Again, as a reminder: Read the Documentation!
___

- first register your app on [twitter apps](https://apps.twitter.com/) and get your settings right (access level and the Callback URL have to be determined!)
- add passport, passport-twitter and express-session packages to your application
- create a file defining a passport strategy (twitter)
- to support login session passport has to serialize and deserialize user
- pass passport to your passport cofiguration and connect both `passport.initialize` and `passport.session` to your app as middleware (make sure that the express-session is used before!)
- set up routes for authenticating and the callback


[Check out my commit on Github after these steps.](https://github.com/DDCreationStudios/votingApp/tree/d398cce56b1df2d042c07d2849223e88a5a2ed7f)

After that, connect the authentication process to your database
___
⭐ Tip: Use for your callback and testing always `http://127.0.0.1:3000/` instead of `http://localhost:3000/`, since it solves a lot of problems, that might occur using passport-twitter. 😉
___
- create a mongoose Schema for your users (to track them in your database)
- fill the callback function of your passport.js file when implementing the twitter strategy, with filtering your database for the user and creating a new one if a user is not existing
- use the connect-mongo package to create a mongoStore and store your sessions in MongoDB
- create a function to test if a user is authenticated and implement it in your desired routes (providing sufficient **authorization**)
- the implementation can look like this:
```javascript
passport.use(
		new Strategy(constants.TWITTER_STRATEGY, (req, token, tokenSecret, profile, cb) => {
  process.nextTick(() => {
    if (!req.user) {
      User.findOne({ 'twitter.id': profile.id }, (err, user) => {
        if (err) return cb(err);
        if (user) {
          if (!user.twitter.token) {
            user.twitter.token = token;
            user.twitter.username = profile.username;
            user.twitter.displayName = profile.displayName;
            user.save(() => {
              if (err) return cb(err);
              return cb(null, user);
            });
          }
          return cb(null, user);
        }

						// if no user is found create one
        const newUser = new User();

        newUser.twitter.id = profile.id;
        newUser.twitter.token = token;
        newUser.twitter.username = profile.username;
        newUser.twitter.displayName = profile.displayName;

        newUser.save(() => {
          if (err) return cb(err);
          return cb(null, newUser);
        });
      });
    } else {
					// when user already exists and is logged in
      const user = req.user;

      user.twitter.id = profile.id;
      user.twitter.token = token;
      user.twitter.username = profile.username;
      user.twitter.displayName = profile.displayName;

      user.save((err) => {
        if (err) return cb(err);
        return cb(null, user);
      });
    }
  });
}),
	);
```

After that your authentication and authorization with twitter is done.

[Check out my commit on Github after these steps.](https://github.com/DDCreationStudios/votingApp/tree/cb96c8b2062f5c634efcba2b258e3ad054799c48)

#### Establish local authentication and authorization

The next step is to authenticate locally. There is actually not much to it, since we have already set up the environment.

- first, update your user schema for local (defining email and password)
- add the bcrypt-nodejs package for securing passwords
- add hashing and validating password methods to your Schema
- then define the routes (this process always clarifies what I actually want to implement)
- here happened actually a main issue, which I was only able to resolve after many, many hours of searching (here the example from the [docs](http://passportjs.org/docs/configure)):
```javascript
app.get('/login', function(req, res, next) {
  passport.authenticate('local', function(err, user, info) {
    if (err) { return next(err); }
    if (!user) { return res.redirect('/login'); }
    req.logIn(user, function(err) {
      if (err) { return next(err); }
      return res.redirect('/users/' + user.username);
    });
  })(req, res, next);
});
```

Only this way, passing in the authentication in the callback function,  provided enough flexibility for displaying errors, but it's very important to create the session explicitly with `logIn()`!

- make sure to differentiate in the routes between signup and login!
- I installed EJS as view engine to actually being able to test my signup and login properly and efficient
- create a logout route, that destroys your session


___
I set so many hours on that Error that I want to display it here again:
`MongooseError: Cast to ObjectId failed for value "favicon.ico" at path "_id"`

I solved it through checking all middleware (there was a major error) and routes. Turned out that setting a route to ('/:pID') is not good when working in development. :D
___

[Check out my commit on Github after the backend setup.](https://github.com/DDCreationStudios/votingApp/tree/30e9627ba3ac2c6b45c64bf2bad4df5726e15a67)

Of course at this point the backend is not perfect. But it's stable enough to go to the next step, the frontend.

Things to do:
- use validation ( with [joi](https://www.npmjs.com/package/joi))
- write unit tests

___

## Frontend

#### Think before you do!

First of all think about what you want to create. Draw out some sketches to visualize what you want to build. Then consider appropriate frameworks.
I will choose React.js and the state management library Redux. The size of this application does NOT necessarily require the use of Redux, however since I want to build it as a single page experience, want to have scalability and like to practice the use of Redux, it's a good fit.

Start planning everything out [thinking in React](https://facebook.github.io/react/docs/thinking-in-react.html).

#### Necessary setup with Babel and Webpack

It's important to realize that Babel and Webpack are not too complicated to set it up yourself. There are so many tutorials for both that you can do it easily yourself.

- add babel for react and es2015 with adding `babel-preset-react babel-preset-es2015` to your dev dependencies (to compile JSX into JS and having all es6 features)
- update your .babelrc file
- update your webpack config and add the react-hot-loader package

At first I want to structure my frontend without the backend in order to connect the whole frontend with the backend at the end. The reason for that is because for now I don't know how my Redux implementation will look like and therefore progressively connecting to the backend wouldn't be efficient.

Therefore:

- restructure your current app.js into an own folder
- create a new app.js as entry point and provide the [basic setup code](https://medium.com/@dabit3/beginner-s-guide-to-react-router-53094349669) for rendering a simple page
- the get the setup working install the react-router, webpack-dev-server and of course react and react-dom packages
- opening a page on the dev-server port should display your react component

[➡️ Check out my commit on Github after the new setup ⬅️](https://github.com/DDCreationStudios/votingApp/tree/9ed98937551ad5eb3208be392040b39c35d4d231)

#### Structure components

I sketched everything out on a paper and came to the conclusion to build 14 components:

- the app component, that hosts everything
- a header
- a footer
- a sidebar
- a signup/login/social media component
- a home screen
- a list of all polls
- the display of a single poll
- a component for the poll and it's answers
- the answers as a list
- the chart
- a 404 page

That's just for the start. I am sure to adapt it when actually programming the app.

#### Design and build components


- first of all I lay out all components and simply style them with materialize css
- remember that styling with React is more complicated than styling normal HTML elements. For simplicity reasons I fix everything with inline styling on the component itself

>Tip: For 100vh on your main content use this inline style on a div, it fits perfectly into the materialize flexbox:
```javascript
style={{
  display: 'flex',
  minHeight: '100vh',
  flexDirection: 'column',
}}
```




- in the process of building components you will slowly get a feeling on how you need to structure your state management with React and Redux



[➡️ Check out my commit on Github after the components are built and styled ⬅️](https://github.com/DDCreationStudios/votingApp/tree/eb17c360e09515f22f8ac38574f576a53855037b)

Now we have to set up React Router to get a basic functionality and feeling for the app:

- enable `historyApiFallback: true` on your webpack dev server to allow proper routing with react router
-





#### Connect React to the Express Backend with React Router

- add the react-router package
- axios?


## Visualization

## Deployment / DevOps

#### Docker



## Useful links & credits
- [📄 "Scotch-IO Passport Authentication"](https://github.com/scotch-io/easy-node-authentication)
- [📄 "Official Passport Site"](http://passportjs.org/)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)



If you gained something from this article let me know with a comment or heart. Make sure to follow for more :)

If you want to support me financially: https://www.paypal.me/DDCreationStudios


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
