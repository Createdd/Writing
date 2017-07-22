# Fetching Gtihub with React and Redux

[<img src="https://images.unsplash.com/photo-1495420047114-9f6ef7fc0cbc?dpr=2&auto=format&fit=crop&w=1199&h=799&q=80&cs=tinysrgb&crop=">](
https://unsplash.com/photos/6IxGFVz0wPM)
https://unsplash.com/photos/6IxGFVz0wPM Photo by Osman Rana on Unsplash

As with everything in life only practice makes you good in a certain field. Therefore I decided to create another application using React and Redux. This time I wanted to focus on asynchronous action flow with Redux, which is a little different from the synchronous dispatching process.


[➡️ Github Repo is available here ⬅️](https://github.com/DDCreationStudios/fetchingReactRedux)


## 📄 Table of contents

<!-- TOC -->

- [Fetching Gtihub with React and Redux](#fetching-gtihub-with-react-and-redux)
  - [📄 Table of contents](#📄-table-of-contents)
  - [What I am going to build](#what-i-am-going-to-build)
  - [The building process](#the-building-process)
  - [The Redux process](#the-redux-process)
  - [Building the search feature with Redux](#building-the-search-feature-with-redux)
  - [Useful links & credits](#useful-links--credits)

<!-- /TOC -->


---
> “Think Big And Don’t Listen To People Who Tell You It Can’t Be Done. Life’s Too Short To Think Small.” - Tim Ferriss
---

## What I am going to build

I am going to build a simple app, that fetches repositories from Github by typing the name of the Github user:

<img src="https://camo.githubusercontent.com/c0b94d5f36a091f0c2e915cec5441045c5aca8ec/687474703a2f2f672e7265636f726469742e636f2f586c6b36696a4a7769432e676966" alt="gif">

## The building process

To quickstart the the configuration I used the [React Slingshot boilerplate](https://github.com/coryhouse/react-slingshot) by Cory House. It provides nice linting and feedback during the whole building process. 

First I started out with defining basic React Components. I used the provided structure and adapted it for a home page and an about page.
For jumping across routes I also used the provided React Router features because it's simple and fast.

The next step was adding some basic styling. I wanted to use Material-UI but quickly realized that I have to dive into the framework. After some minutes with bugs, I decided to stay with [MaterializeCSS](http://materializecss.com/getting-started.html), which I used in the past. It provides great documentation and simple CSS components. It's the CSS framework I enjoy working with the most. 



## The Redux process

After that I wired up a basic Redux flow, providing a store, actions and a reducer. One way when working [async in Redux](http://redux.js.org/docs/advanced/) is to use [redux-thunk](https://github.com/gaearon/redux-thunk). I have choosen this way because it's fast and reliable. (I didn't want to tackle Redux-Saga, since I need more knowledge on Promises)

From redux-thunk's docs: 
>Redux Thunk middleware allows you to write action creators that return a function instead of an action. The thunk can be used to delay the dispatch of an action, or to dispatch only if a certain condition is met. The inner function receives the store methods dispatch and getState as parameters.

That's the whole magic. Returning a function instead an action. It allows to wait for an answer after a http call (or whatever call) and dispatching the action after receiving the data.

The code looked like: 

```javascript
//Action
import axios from 'axios';
import * as types from './actionTypes';

export function loadReposSuccess(repos) {
	return {
		type: types.LOAD_REPOS_SUCCESS,
		repos
	};
}

export function loadRepos() {
	return function(dispatch) {
		return axios
			.get('https://api.github.com/users/DDCreationStudios/repos')
			.then(repos => {
				dispatch(loadReposSuccess(repos.data));
				console.warn(repos.data);
			})
			.catch(err => {
				throw err;
			});
	};
}

```

```javascript
//index.js
import React from 'react';
import { render } from 'react-dom';
import { Router, browserHistory } from 'react-router';
import 'materialize-css/dist/css/materialize.min.css';
import { Provider } from 'react-redux';

import routes from './routes';
import configureStore from './store/configureStore';
import { loadRepos } from './actions/reposAction';

const store = configureStore();
store.dispatch(loadRepos());

render(
	<Provider store={store}>
		<Router history={browserHistory} routes={routes} />
	</Provider>,
	document.getElementById('app')
);

```

```javascript
//reducer
import * as types from '../actions/actionTypes';

export default function reposReducer(state = [], action) {
	switch (action.type) {
		case types.LOAD_REPOS_SUCCESS: {
			return action.repos;
		}
		default:
			return state;
	}
}
```

>On a side note: I used [axios](https://www.npmjs.com/package/axios) because I initially thought I would create a bigger app. A simple "fetch" method would have been sufficient as well. :)


## Building the search feature with Redux

This was a little bit more complicated, since I needed to make the fetch depended on another user action. But that's why Redux is so great.

The key thing was to regulate the flow with the store in the index.js, because I wanted to subscribe to the store and only dispatch an action when a certain change in state has occured. I found the "handleChange" helper function as solution:


```javascript
//index.js
import React from 'react';
import { render } from 'react-dom';
import { Router, browserHistory } from 'react-router';
import 'materialize-css/dist/css/materialize.min.css';
import { Provider } from 'react-redux';

import routes from './routes';
import configureStore from './store/configureStore';
import { loadRepos } from './actions/reposAction';

let currentValue;
function handleChange() {
	let previousValue = currentValue;
	currentValue = store.getState().user;

	if (previousValue !== currentValue) {
		store.dispatch(loadRepos(store.getState().user));
	}
}

const store = configureStore();
store.dispatch(loadRepos(store.getState().user));
store.subscribe(handleChange);

render(
	<Provider store={store}>
		<Router history={browserHistory} routes={routes} />
	</Provider>,
	document.getElementById('app')
);
```

Now the fetching of data was called only when the state of user changed in the store. Heureka! 

Then I adapted the other files accordingly:


```javascript
//reducer index.js

import { combineReducers } from 'redux';

import repos from './reposReducer';
import user from './userReducer';

const rootReducer = combineReducers({
	repos,
	user
});

export default rootReducer;
```

```javascript
//initialState.js
export default {
	repos: [],
	user: 'DDCreationStudios'
};
```

```javascript
//updated repo reducer
import * as types from '../actions/actionTypes';
import initialState from './initialState';

export default function reposReducer(state = initialState.repos, action) {
	switch (action.type) {
		case types.LOAD_REPOS_SUCCESS: {
			return action.repos;
		}
		default:
			return state;
	}

```

```javascript
//user reducer
import * as types from '../actions/actionTypes';
import initialState from './initialState';

export default function userReducer(state = initialState.user, action) {
	switch (action.type) {
		case types.LOAD_USER_SUCCESS: {
			return action.user;
		}
		default:
			return state;
	}
}
```

```javascript
//user action
import axios from 'axios';
import * as types from './actionTypes';

export function loadUser(user) {
	return {
		type: types.LOAD_USER_SUCCESS,
		user
	};
}
```

```javascript
//updated repo action
import axios from 'axios';
import * as types from './actionTypes';

export function loadReposSuccess(repos) {
	return {
		type: types.LOAD_REPOS_SUCCESS,
		repos
	};
}

export function loadRepos(user) {
	return function(dispatch) {
		return axios
			.get(`https://api.github.com/users/${user}/repos`)
			.then(repos => {
				dispatch(loadReposSuccess(repos.data));
				console.log("receiving following data: "+repos.data);
			})
			.catch(err => {
				throw err;
			});
	};
}
```

```javascript
//actionTypes
export const LOAD_REPOS_SUCCESS = 'LOAD_REPOS_SUCCESS';
export const LOAD_USER_SUCCESS = 'LOAD_USER_SUCCESS';
```




## Useful links & credits
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)



If you gained something from this article let me know with a comment or heart. Make sure to follow for more :)


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
