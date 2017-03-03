# Fast guide of the Todo App in React and Redux ⚛ ⏩

[<img src="https://images.unsplash.com/1/work-station-straight-on-view.jpg?dpr=2&auto=format&fit=crop&w=767&h=511&q=80&cs=tinysrgb&crop=" alt="https://unsplash.com/photos/xII7efH1G6o">](https://unsplash.com/photos/xII7efH1G6o) https://unsplash.com/photos/xII7efH1G6o


Building the Todo List Example with React and Redux. I found the documentation not good enough - so here is another approach to introduce the famous basic app.

See my [Github Repo](https://github.com/DDCSLearning/reduxTodo) for actual code (Using create-react-app, redux, [ducks](https://github.com/erikras/ducks-modular-redux)).

<img src="https://raw.githubusercontent.com/reactjs/redux/master/logo/logo.png" alt="react logo" height="200" align="right"/>
<img src="https://facebook.github.io/react/img/logo.svg" alt="react logo" height="200"/>


## 📄 Table of contents



---

>"In the business world, the rearview mirror is always clearer than the windshield."
― [Warren Buffett](https://de.wikipedia.org/wiki/Warren_Buffett)

---


## 1. Before writing code

Think about what you want to achieve in your app.
As always [think in React](https://facebook.github.io/react/docs/thinking-in-react.html)! Have an idea how your app is structured with components. Also decide which components have a presentational function (mainly for presenting data) and which have a container function (providing data and behavior). Check [Dan Abramov's article](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0#.24ud80eei) for more.

## 2. Write your basic components outlay

Find the [code](http://redux.js.org/docs/basics/ExampleTodoList.html) a Facebook's example.

If that's already overwhelming start with the basics.

Cut down you need:
1. an input field with a button (AddTodo)
1. a list that renders the todo items (TodoList)
1. and additionally a filter component that shows your items accordingly (Filter)

## 3. Get Redux input
In previous articles we learned what `State` is all about. It's data that changes and cannot or should not be passed via props.
Also, remember `Actions` from Redux, which are events from user interaction.

Revisit your components and think about theirs State and Actions:
- AddTodo: No State is needed, since data doesn't change based on input. The components allows to add items - that's the action.
-



## Conclusion



```
Please leave comments, feedback and suggestions as I am always trying to improve.
Share your thoughts - it's never been easier 😄
```

## Useful links & credits
- [🌐 "React" - Facebook (official site)](https://facebook.github.io/react/)
- [🌐 "Redux" - Facebook (official site)](http://redux.js.org/)
- [📄 "Build React apps using mocks" - rajaraodv (8min article)](https://medium.com/@rajaraodv/step-by-step-guide-to-building-react-redux-apps-using-mocks-48ca0f47f9a#.nyiqb1biq)
- [📄 "Ducks file structure for Redux" - S.C.Barrus (3min article)](https://medium.com/@scbarrus/the-ducks-file-structure-for-redux-d63c41b7035c#.305a6da9k)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
