# ⚛ 💡  Getting started with React

[<img src="https://images.unsplash.com/photo-1466951561471-9a9a7b99cd77?dpr=2&auto=format&fit=crop&w=767&h=513&q=80&cs=tinysrgb&crop=" alt="https://unsplash.com/photos/uD1ieQvG81c">](https://unsplash.com/photos/uD1ieQvG81c)


[React](https://facebook.github.io/react/) is `a Jacascript library for building user interfaces`. I'll go into the topic and clarify some features to get the most out of my coding with React.

Covering: ES6 React, virtual DOM, Component-driven development, Immutability, Top-down rendering, , debugging, routing, isomorphic React.

<img src="https://facebook.github.io/react/img/logo.svg" alt="react logo" height="200" align="right">

## 📄 Table of contents


<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [⚛ 💡  Getting started with React](#getting-started-with-react)
  * [📄 Table of contents](#table-of-contents)
  * [1. Components & Props  🔻](#1-components-props)
      * [High-order component](#high-order-component)
      * [Uncontrolled components ➡️](#uncontrolled-components-️httpsfacebookgithubioreactdocsuncontrolled-componentshtml)
      * [In terms of `props`:](#in-terms-of-props)
      * [Routing in React](#routing-in-react)
  * [2. State and Lifecycle 🔻](#2-state-and-lifecycle)
      * [Lifecycle](#lifecycle)
  * [3. Events 🔻](#3-events)
  * [4. (Conditional) rendering 🔻](#4-conditional-rendering)
  * [5. Lifting State 🔻](#5-lifting-state)
  * [6. Compositions & Inheritance 🔻](#6-compositions-inheritance)
  * [Conclusion](#conclusion)
  * [Useful links & credits](#useful-links-credits)

<!-- tocstop -->



---

>"I have not failed. I've just found 1000 ways that won't work."
― [Thomas Edison,  Prolific Inventor](https://en.wikipedia.org/wiki/Thomas_Edison)

---


## 1. Components & Props  🔻
>Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called "props") and return React elements describing what should appear on the screen.

The difference between functional components and class components, is that functional components simply take props and provide a function, whereas a class allows many more features.

It is possible to compose or extract components to achieve the desired functional structure.

#### High-order component
>Concretely, a higher-order component is a function that takes a component and returns a new component.
>HOCs are common in third-party React libraries, such as Redux's connect and Relay's createContainer.

[High-order components (HOCs)](https://facebook.github.io/react/docs/higher-order-components.html) are more advanced and are useful for:
- Code reuse, logic and bootstrap abstraction
- Render Highjacking (HOC takes control of the render output of the WrappedComponent)
- State abstraction and manipulation
- Props manipulation

Check out [this article ⬆️](https://medium.com/@franleplant/react-higher-order-components-in-depth-cf9032ee6c3e#.yce1tzuw6) for more.

[Jack Franklin sums it up:](https://www.sitepoint.com/react-higher-order-components/)
>By creating higher order components you’re able to keep data defined in only one place, making refactoring easier. Higher order function creators enable you to keep most data private and only expose pieces of data to the components that really need it. By doing this you make it obvious which components are using which bits of data, and as your application grows you’ll find this beneficial.

#### Uncontrolled components [➡️](https://facebook.github.io/react/docs/uncontrolled-components.html)

>The alternative is uncontrolled components, where form data is handled by the DOM itself.
>To write an uncontrolled component, instead of writing an event handler for every state update, you can use a ref to get form values from the DOM.

#### In terms of `props`:

> ❗ All React components must act like pure functions with respect to their props. ❗

This means that component is not allowed to modify it's own props.

#### Routing in React
Get familiar with the [react-router API](https://github.com/ReactTraining/react-router/blob/master/docs/API.md#redirect) since it provides a very easy and sufficient way of routing components on the client-side (but is also able to render on server-side!)
Check out this great [introduction](https://medium.com/@dabit3/beginner-s-guide-to-react-router-53094349669#.uyatb25eu) if you are not familiar with it.

## 2. State and Lifecycle 🔻

#### Lifecycle
>Each component has several "lifecycle methods" that you can override to run code at particular times in the process. Methods prefixed with will are called right before something happens, and methods prefixed with did are called right after something happens.

The following [method types](https://facebook.github.io/react/docs/react-component.html#constructor) are available:
- Render
- Mounting
- Updating
- Unmounting
- Class Properties (defaultProps, displayName, propTypes)
- Instance Properties (props, state)
- Other (setState, forceUpdate)

>React.Component is an abstract base class, so it rarely makes sense to refer to React.Component directly. Instead, you will typically subclass it, and define at least a render() method.

**Notes on common methods:**

- `render()` is required and should be "pure", which means that it should not modify the component's state.
- `constructor()` is called *before* it is mounted.
- `componentWillMount()` is invoked immediately before mounting occurs.
- `componentDidMount()` is invoked immediately after a component is mounted.
- Use `shouldComponentUpdate()` to let React know if a component's output is not affected by the current change in state or props.
- `componentWillUpdate()` is invoked immediately before rendering when new props or state are being received.
- `setState()` performs a shallow merge of nextState into current state.
- `defaultProps()` can be defined as a property on the component class itself, to set the default props for the class.
- `propTypes` can be defined as a property on the component class itself, to define what types the props should be.
- `this.props` contains the props that were defined by the caller of this component.
- `this.props.children` is a special prop, defined by the child tags in the JSX expression rather than in the tag itself.


## 3. Events 🔻
## 4. (Conditional) rendering 🔻
## 5. Lifting State 🔻
## 6. Compositions & Inheritance 🔻


## Conclusion




```
Please leave comments, feedback and suggestions as I am always trying to improve.
Share your thoughts - it's never been easier 😄
```

## Useful links & credits
- [📄 "The React Way" - RisingStack (article)](https://blog.risingstack.com/the-react-way-getting-started-tutorial/)
- [🌐 "React" - Facebook (official site)](https://facebook.github.io/react/)
- [📄 "Beginner's guide to React Routing"- Nader Dabit (11min article)](https://medium.com/@dabit3/beginner-s-guide-to-react-router-53094349669#.uyatb25eu)
- [📄 "HOCs in depth" - franleplant (10min article)](https://medium.com/@franleplant/react-higher-order-components-in-depth-cf9032ee6c3e#.yce1tzuw6)
- [📄 "React HOCs" - Sitepoint /Jack Franklin (article)](https://www.sitepoint.com/react-higher-order-components/)
- [🔀 "Model"](hasfd)
- [🔀 "Model"](hasfd)
- [🔀 "Model"](hasfd)


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
