# How to fetch Images from Unsplash.com in React
[<img src="https://images.unsplash.com/photo-1497493292307-31c376b6e479?dpr=2&auto=format&fit=crop&w=1199&h=799&q=80&cs=tinysrgb&crop=&bg=">](
https://unsplash.com/photos/k_T9Zj3SE8k)
https://unsplash.com/photos/k_T9Zj3SE8k

Since Unsplash.com released their API and I just love their content, I decided to write a short article on how to use it with React. Unsplash is awesome! :) Enjoy.

[➡️ Github Repo is available here ⬅️](https://github.com/DDCreationStudios/fetchingInReact)

---
>"Everything negative - pressure, challenges - is all an opportunity for me to rise." - Kobe Bryant
---

## 📄 Table of contents

  * [📄 Table of contents](#table-of-contents)
  * [Set up basics](#set-up-basics)
  * [Fetch data with the fetch API](#fetch-data-with-the-fetch-api)
  * [Fetch data using a library (like Axios)](#fetch-data-using-a-library-like-axios)
  * [Add search feature](#add-search-feature)
  * [Polish up React code](#polish-up-react-code)
  * [Adapt to Unsplash guidelines](#adapt-to-unsplash-guidelines)
  * [Useful links & credits](#useful-links-credits)


## Set up basics

To set up the basics, I use the code base from another project I did, using:

- create-react-app
- React components that render images in a list

## Fetch data with the fetch API

- use  the [fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) like:

```javascript
componentDidMount() {
	fetch('https://api.unsplash.com/photos/?client_id=' + cred.APP_ID)
		.then(res => res.json())
		.then(data => {
			this.setState({ imgs: data });
		})
		.catch(err => {
			console.log('Error happened during fetching!', err);
		});
}
```
- use 'componentDidMount' lifecycle when fetching data (DOM is represented)
- describe a fetch method using Promise functionality
- transform the call into a JSON object and pass it into state
- after that, simply render out each image from the fetched link

[➡️ See the Github Repo after those steps ⬅️](https://github.com/DDCreationStudios/fetchingInReact/tree/basicFetch)

## Fetch data using a library (like Axios)

Fetching can also be accomplished by one of many libraries. I will use [axios](https://github.com/mzabriskie/axios), since it provides cool features like:
- Make XMLHttpRequests from the browser
- Make http requests from node.js
- Supports the Promise API
- Intercept request and response
- Transform request and response data
- Cancel requests
- Automatic transforms for JSON data
- Client side support for protecting against XSRF

So the next steps are:
- add the axios package
- simply adapt the fetch method to the methods from the axios package

```javascript
componentDidMount() {
	axios
		.get('https://api.unsplash.com/photos/?client_id=' + cred.APP_ID)
		.then(data => {
			this.setState({ imgs: data.data });
		})
		.catch(err => {
			console.log('Error happened during fetching!', err);
		});
}
```

Very easy and works well:)

[➡️ See the Github Repo after those steps ⬅️](https://github.com/DDCreationStudios/fetchingInReact/tree/basicFetch)

#### Looks like this:
<img src="../assets/RFETCH/Screenshot1.png" alt=""/>

## Add search feature

- adapt your fetched link (add query and search parameters)
- make your request dynamic, connecting the search query to your app
- add a searchbar component
- make sure to bind all methods (use the arrow functions or bind them manually)

```javascript
performSearch = query => {
  axios
    .get(
      `https://api.unsplash.com/search/photos/?page=1&per_page=10&query=${query}&client_id=${cred.APP_ID}`
    )
    .then(data => {
      this.setState({ imgs: data.data.results });
    })
    .catch(err => {
      console.log('Error happened during fetching!', err);
    });
};
```

## Polish up React code

- use the ref-attribute for the input
```javascript
this.props.onSearch(this.query.value);
---
ref={input => (this.query = input)}
```

-  set a default for your performSearch method and put the performSearch into the componentDidMount lifecycle
- render out a different component when no images can be found with an if statement
- use conditional rendering to render a paragraph when the fetch is not finished (setting a flag to the state and changing it in the fetch method)

```javascript
<div className="main-content">
	{this.state.loadingState
		? <p>Loading</p>
		: <ImgList data={this.state.imgs} />}
</div>
```


[➡️ See the Github Repo after those steps ⬅️](https://github.com/DDCreationStudios/fetchingInReact/tree/axiosSearch
)

___
⭐ That was incredible easy and already shows how much you can do with the API :)
___

## Adapt to Unsplash guidelines

When using an API always, ALWAYS, make sure to read their guidelines.
➡️ [Unsplash API guidelines](https://community.unsplash.com/developersblog/unsplash-api-guidelines)

So as an example here, I didn't credit Unsplash or the photographer. Therefore I have to improve my app by retrieving more information from the data and adding credits to the owners:

```javascript
const Img = props =>
	<li>
		<a href={props.link}>
			<img src={props.url} alt="Unsplash Image here" />
		</a>
		<p>
			Photo by
			<a href={props.user}>{props.name}</a>
			<a href={props.link}> See on Unsplash</a>
		</p>
	</li>;
```

#### Now it looks like

<img src="../assets/RFETCH/Screenshot2.png" alt=""/>



[➡️ See the finished app on Github ⬅️](https://github.com/DDCreationStudios/fetchingInReact
)


## Useful links & credits

- [Unsplash.com](https://unsplash.com/)
- I did a treehouse course, that covers an app with a similar approach:

<a href="http://referrals.trhou.se/danieldeutsch3" target="_blank"><img src="https://static.teamtreehouse.com/assets/content/referral-badge-grn.png" height="200"/></a>

If you gained something from this article let me know with a comment or heart. Make sure to follow for more :)


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
