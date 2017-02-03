# 🛠 📐📏 Understanding MVC Architecture with React

[<img src="https://images.unsplash.com/photo-1484504844383-7676f295d034?dpr=2&auto=format&fit=crop&w=767&h=431&q=80&cs=tinysrgb&crop=">](https://unsplash.com/search/architecture?photo=b6GavtrLBo4)


Model-View-Controller (MVC) is a very often used software design pattern for implementing user interfaces. Since I tried to use and understand the structure in my last projects, I decided to take a deeper look into it. This article provides an **overview** of MVC and it's use in the React environment.

## 📄 Table of contents
  * [What is MVC?](#what-is-mvc)
  * [What are it's advantages and disadvantages for coding?](#what-are-its-advantages-and-disadvantages-for-coding)
  * [What is React?](#what-is-react)
  * [Apply MVC with React = Flux?](#apply-mvc-with-react-flux)
    * [What is Flux und what is different compared to MVC?](#what-is-flux-und-what-is-different-compared-to-mvc)
    * [What is Redux und what is different compared to Flux?](#what-is-redux-und-what-is-different-compared-to-flux)
  * [Dive deeper - some useful links](#dive-deeper-some-useful-links)

---

>"If you can't understand it, you can't change it"
― [Eric Evans, Technologist](https://en.wikipedia.org/wiki/Domain-driven_design)

---

### What is MVC?
MVC is a way of thinking to structure your web application. It's popular because it's used by many frameworks that implement that structure (rails, cakephp, django etc.).
The architecture stems from the traditional flow of a web application.

<img src="http://i.imgur.com/fPHzoBY.png" align="right" height="300">

  1. **View - Client**

  Displays visualization of the data to the user. Only connected to the controller.
  2. **Controller - Server**

  Processes server-side logic and acts as a middleware between View and Model, i.e. controlling the flow of data.
  3. **Model - Database**

  Processing data from or to the database. Only connected to the controller.

See a practical example [here ➡️](https://www.tutorialspoint.com/design_pattern/mvc_pattern.htm)

### What are it's advantages and disadvantages for coding?
The structure allows flexibility since responsibilities are clearly separated. This leads to
- better and easier code maintenance and reusability
- easier to coordinate in teams due to the separation
- ability to provide multiple views
- support for asynchronous implementations

, but also to
- an increased complex setup process
- dependencies, i.e. changes in the model or controller affect the whole entity

### What is React?
[React](https://github.com/facebook/react) is JavaScript library from Facebook, that is designed to create interactive UIs. The main features are that it's
- declarative: Design different views for each state, which will be efficiently updated and re-rendered
- component-based: Build components, that manage their own state and structure them together into more complex UIs
- maintains an internal representation of the rendered UI ("virtual DOM"), that renders only the changed elements

### Apply MVC with React = Flux?

Whereas React is often referred to as the View in a MVC structure, Facebook presented their own architecture called [Flux ➡️](https://github.com/facebook/flux). The problem with a MVC structure is it's bidirectional communication, which proved to be very hard to debug and understand when a change in one entity caused cascading effect across the codebase. Especially when the app is scaling into a much bigger one, like Facebook for example. The flow of data was not well enough or easy enough defined for large applications.

<img src="https://github.com/facebook/flux/blob/master/docs/img/flux-diagram-white-background.png?raw=true" align="right" alt="flux diagram">

#### What is Flux und what is different compared to MVC?
[Flux](https://github.com/facebook/flux) is made up of 4 key elements:
  1. **Actions**

  Objects with property and data.
  2. **Stores**

  Contain the application's state and logic.
  3. **The Dispatcher**

  Processes registered actions and callbacks.
  4. **Views**

  Listen to changes from the stores and re-render themselves.

It's important to notice and understand the unidirectional flow here.

Now the differences to a MVC are:
- The flow of processing is unidirectional instead of bidirectional
- stores are able to store any application related state, whereas the model in MVC was designed to store single objects
- the initiating point Dispatcher makes debugging much easier

Despite the fact that some are calling MVC "dead", I think Flux is more of a refined and enhanced MVC, and thus sympathizing with [Paul Shan and his conclusion in his article.](http://voidcanvas.com/flux-vs-mvc/)

#### What is Redux und what is different compared to Flux?
Redux builds on Flux and can be described in [three fundamental principles](http://redux.js.org/docs/introduction/ThreePrinciples.html):
  1. **Only one single source of truth**

  The state of your entire application is stored in a **single** store.
  2. **State is read-only**

  The only way to change the state is to emit an **action** (an object describing what happened).
  3. **Changes are made with pure functions**3.

  Specify the transformation by actions with **reducers**, which allow to navigate through states.

[Now what's different to Flux?](http://redux.js.org/docs/introduction/PriorArt.html)
- Redux does not have the concept of a *dispatcher* because it relies on pure functions instead of event emitters.
- Redux assumes you never mutate your data. You dont mutate them in a reducer but rather return a new object

```
Please leave comments, feedback and suggestions as I am always trying to improve.
Share your thoughts - it's never been easier 😄
```

### Dive deeper - some useful links
- **MVC**
- [🔀"Model-View-Controller" - Microsoft (retired content!)](https://msdn.microsoft.com/en-us/library/ff649643.aspx)
- [🔀"What is programming MVC" - DevMarketer (video)](https://www.youtube.com/watch?v=1IsL6g2ixak)
- [🔀"MVC Pattern" - Tutorialspoint (practical example)](https://www.tutorialspoint.com/design_pattern/mvc_pattern.htm)
- [🔀"Benefits of Using MVC Model" - Soroosh Pardaz (LinkedIn article)](https://www.linkedin.com/pulse/six-benefits-using-mvc-model-effective-web-soroosh-pardaz)
- [🔀"Is MVC dead on the front end?" - Alex Moldovan (5min article)](https://medium.freecodecamp.com/is-mvc-dead-for-the-frontend-35b4d1fe39ec#.5h3n45u4b)
- **Flux**
- [🔀"Flux Concepts" - Facebook (Github)](https://github.com/facebook/flux/tree/master/examples/flux-concepts)
- [🔀"Flux vs MVC Design Patterns" - Amir Salihefendic (5min article)](https://medium.com/hacking-and-gonzo/flux-vs-mvc-design-patterns-57b28c0f71b7#.g4rga64ez)
- [🔀"MVC does not scale" - Abel Avram (5min article)](https://www.infoq.com/news/2014/05/facebook-mvc-flux)
- **Redux**
- [🔀"Flux vs MVC" - Paul Shan (5min article)](http://voidcanvas.com/flux-vs-mvc/)
- [🔀"Redux Docs" - Redux (complete documentation)](http://redux.js.org/)
