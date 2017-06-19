# Rate Questions with React and Redux - A baby example 👶
[<img src="https://images.unsplash.com/photo-1497562424514-9bf21ad16ffe?dpr=2&auto=format&fit=crop&w=1080&h=608&q=80&cs=tinysrgb&crop=&bg=">](
https://unsplash.com/photos/s0XDLfhyN34)
https://unsplash.com/photos/s0XDLfhyN34

I will build a small application for simply rating questions. This is designed as an exercise project for React and Redux, since I am still not understanding it.

[➡️ Github Repo is available here ⬅️](https://github.com/DDCreationStudios/)


## 📄 Table of contents

  * [Motivation for this article](#motivation-for-this-article)
  * [Modularizing the base](#modularizing-the-base)
  * [Adding Redux](#adding-redux)
      * [Action Types](#action-types)
      * [Reducers](#reducers)
      * [Actions and Action Creators](#actions-and-action-creators)
      * [Create the Redux Store](#create-the-redux-store)
      * [Connect the container to the store](#connect-the-container-to-the-store)
  * [Add another component in the Redux App](#add-another-component-in-the-redux-app)
  * [Chrome Redux DevTools](#chrome-redux-devtools)

---
>"Everything is practice." - Pele
---

## Motivation for this article

Another small application to understand Redux and React. It feels like it's the 100th app trying to grasp Redux. But 1 month without Redux and you start at basically nothing again. I am like: "Yeah I have heard about that" - and that's it. Action, Action Creators, Reducers, Dispatch, blabla. Too many things to understand :D So once again ↗️

## Modularizing the base

Structure the components in order to fit perfectly into a Redux application.


[➡️ Codebase on Github ⬅️](https://github.com/DDCreationStudios/questionScores/tree/ad0543f1d6607048482ecec409041a3b3329e80d)

- the stopwatch component has it's own local state is not dependent on other components
- the stats and counter components are dependent on other components
- the AddQuestionForm is dependent on other components and also contains logical information
- the header and question components

Modularizing helps to
- isolate responsibilities, which means easier testing and debugging
- better scale the app and easier for the use of Redux
- better organize between teams


[➡️ Modularized Code on Github ⬅️](https://github.com/DDCreationStudios/questionScores/tree/fe8fd2a45b6c3c4129d7abb970541d3f2541147b)

## Adding Redux

#### Action Types

Decide which components should take part in the Redux store.
-> In this application only the questions have to be made available to all components.

Find what events happen in your application for this specific state. -> In this application it is
- changing the score
- adding questions
- removing questions

#### Reducers

Reducers are pure functions, that change state according to the action type.

The reducer function provides different switch statements on how change the state. (Make sure to never change the state itself! It should be a pure function! #immutability)

For example:
```javascript
export default function Player(state = initialState, action) {
  switch (action.type) {
    case QuestionActionTypes.ADD_PLAYER:
      return [
        ...state,
        {
          name: action.name,
          score: 0,
        },
      ];
    case QuestionActionTypes.REMOVE_QUESTION:
      return [...state.slice(0, action.index), ...state.sclice(action.index + 1)];
    case QuestionActionTypes.UPDATE_QUESTION_SCORE:
      return state.map((question, index) => {
        if (index === action.index) {
          return {
            ...question,
            score: question.score + question.score,
          };
        }
        return question;
      });
    default:
      return state;
  }
}
```

#### Actions and Action Creators

Submiting an action to Redux
- action creators generate an action (action = an event that will result in a change in state)
- action is dispatched to the Redux store
- a reducer passes the action to a component and returns the new state

For example for adding a question:
```javascript
export const addQuestion = name => ({
  type: QuestionActionTypes.ADD_QUESTION,
  name,
});
```

#### Create the Redux Store

Create a store in your index.js passing it the main reducer and wrap it around your scoreboard component in order to provide the store to the whole application.

#### Connect the container to the store

- use `mapStateToProps` to assign the state to a prop value -> assign the state of the questions as props
- for automatically dispatching actions, that are created use:

```javascript
const {dispatch, questions} = this.props;
const addQuestion = bindActionCreators(QuestionActionCreators.addQuestion, dispatch);
const removeQuestion = bindActionCreators(QuestionActionCreators.removeQuestion, dispatch);
const updateQuestionScore = bindActionCreators(QuestionActionCreators.updateQuestionScore, dispatch);
```

- update the event handlers on the components accordingly (counter, question and scoreboard components)
- the header and stopwatch components don't need changes, because they do not participate in the Redux cycle

## Add another component in the Redux App

Now we want to display details to each question

- add a new action type (select a question)
- extend the reducer with a new switch case and additional state
- add a new action creator for selecting a question
- create a new bindActionCreator in the scoreboard component
- update mapStateToProps with the selected question index
- create a QuestionDetail component to display details
- update the event handler on the question component

<img src="../assets/REDSCORE/Screenshot2.png" alt="" />

[➡️ See the commit with the implementation of the detail component on Github ⬅️](https://github.com/DDCreationStudios/questionScores/commit/e23757d34620b8a5f6c5aac9d0fe63dba621c5ca)


## Chrome Redux DevTools

- Download the [Redux DevTools Extension](https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd)
- add the necessary line of code to your store

```javascript
const store = createStore(
	QuestionReducer,
	window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__(),
);
```

The DevTools help to develop and debug your Redux app. Check out this [article](https://medium.com/@zalmoxis/improve-your-development-workflow-with-redux-devtools-extension-f0379227ff83) for more.

<img src="../assets/REDSCORE/Screenshot1.png" alt="" />



___
[➡️ Result on Github ⬅️](https://github.com/DDCreationStudios/questionScores)
___

If you gained something from this article let me know with a comment or heart. Make sure to follow for more :)


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
