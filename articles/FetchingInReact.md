# How to fetch Images from Unsplash.com in React
[<img src="https://images.unsplash.com/photo-1497493292307-31c376b6e479?dpr=2&auto=format&fit=crop&w=1199&h=799&q=80&cs=tinysrgb&crop=&bg=">](
https://unsplash.com/photos/k_T9Zj3SE8k)
https://unsplash.com/photos/k_T9Zj3SE8k

Since Unsplash.com released their API and I just love their content, I decided to write a short article on how to use it. Enjoy.

[➡️ Github Repo is available here ⬅️](https://github.com/DDCreationStudios/fetchingInReact/tree/basicFetch)


## 📄 Table of contents


<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [How to fetch Images from Unsplash.com in React](#how-to-fetch-images-from-unsplashcom-in-react)
  * [📄 Table of contents](#table-of-contents)
  * [Set up basics](#set-up-basics)
  * [Fetching data](#fetching-data)
      * [Using easy fetch link](#using-easy-fetch-link)
      * [Fetch data using a library (like Axios)](#fetch-data-using-a-library-like-axios)
      * [Using the Unsplash.js library](#using-the-unsplashjs-library)
  * [Useful links & credits](#useful-links-credits)

<!-- tocstop -->

## Set up basics

To set up the basics, I use the code base from another project I did:

- (treehouse gif searcher)
- create-react-app
- eslint with [equimper extension](https://github.com/EQuimper/eslint-config-equimper)
- simply setting up React components that render images in a list

## Fetching data

#### Using easy fetch link

- use fetch like:

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

#### Fetch data using a library (like Axios)

Fetching can also be accomplished by one of many libraries. I will use
[axios](https://github.com/mzabriskie/axios). Since it provides cool features like:
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
-

#### Using the Unsplash.js library

- add the [unsplash-js](https://github.com/unsplash/unsplash-js) package
- add your [developer credentials](https://unsplash.com/developers) from Unsplash
- I'll use the [dotenv package](https://www.npmjs.com/package/dotenv) to hide my credentials

-





---
>"Everything negative - pressure, challenges - is all an opportunity for me to rise." - Kobe Bryant
---

##

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



If you gained something from this article let me know with a comment or heart. Make sure to follow for more :)


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
