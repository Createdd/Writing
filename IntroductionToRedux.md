# ⚛ 💡 🏁 8 steps to get started with Redux - A roadmap

[<img src="https://images.unsplash.com/photo-1476445704028-a36e0c798192?dpr=2&auto=format&fit=crop&w=767&h=511&q=80&cs=tinysrgb&crop=">](https://unsplash.com/photos/NFs6dRTBgaM)

In ["Understanding MVC Architecture with React"](https://medium.com/@ddcreationstudi/understanding-mvc-architecture-with-react-6cd38e91fefd#.r66jqp0ly) I came to the conclusion that redux seems to be the perfect fit for structuring apps with react. Now I want to provide a roadmap on how to use it in practice.
As a reminder: Redux is builds on Flux as a refined MVC pattern and allows to manage state out of one hand.

## 📄 Table of contents 🔻


---

>"In theory there's no difference between theory and practice. But, in practice, there is."
― [Jan L. A. Van De Snepscheut, Computer Scientist](https://en.wikiquote.org/wiki/Jan_L._A._van_de_Snepscheut)

---

## 1. Set up your environment 🔻
Set up your desired environment. [React boilerplates ➡️](http://andrewhfarmer.com/starter-project/) are a great way to get going. Be sure to understand the according bundler at least a little bit.

## 2. Set up your components and Layout 🔻
When creating your Components and how the fit together remind yourself to [think in React](https://facebook.github.io/react/docs/thinking-in-react.html).

## 3. Set up routing 🔻
React Router is the perfect tool for switching content components in your main components. Get yourself comfortable with the [React Docs](https://facebook.github.io/react/docs/react-api.html). And first of all how to handle and fit elements together (e.g. transforming elements will `Clone and return a new React element using element as the starting point. The resulting element will have the original element's props with the new props merged in shallowly.`).
>[React Router](https://github.com/ReactTraining/react-router/blob/master/docs/Introduction.md) is a powerful routing library built on top of React that helps you add new screens and flows to your application incredibly quickly, all while keeping the URL in sync with what's being displayed on the page.

Be sure to include `this.props.children` in your main component that is rendered in your main path, so props can be passed downwards.

## 4. Set up Redux store 🔻

[<img src="http://jslancer.com/wp-content/uploads/2016/09/rre-2.png" alt="credit to http://jslancer.com/2016/09/28/migrating-my-first-angularjs-app-to-reduxangularjs/" height="200" align="left">](http://jslancer.com/2016/09/28/migrating-my-first-angularjs-app-to-reduxangularjs/)
🔖 Image credit to  http://jslancer.com/2016/09/28/migrating-my-first-angularjs-app-to-reduxangularjs/
- create a (default)state
- create a [store](http://redux.js.org/docs/api/createStore.html)
- if you want to sync history with store, use [syncHistoryWithStore](https://www.npmjs.com/package/react-router-redux)



## 5. Plan Redux Actions and Reducers 🔻
## 6. Integrate Store with React Router 🔻
## 7. Updating State with Reducers 🔻
## 8. Debugging 🔻


### What is Redux?

## Conclusion

```
Please leave comments, feedback and suggestions as I am always trying to improve.
Share your thoughts - it's never been easier 😄
```

## Dive deeper - some useful links
- **For setup**
- [🔀 "Learn Redux" - Wes Bos (Great Video Tutorial)](https://learnredux.com/)
- [🔀 "List of React Starter Prjects" - Andrew H Farmer](http://andrewhfarmer.com/starter-project/)
- [🔀 "Thinking in React" - facebook](https://facebook.github.io/react/docs/thinking-in-react.html)
- [🔀 "Model"](hasfd)
- [🔀 "Model"](hasfd)
- [🔀 "Model"](hasfd)




<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
