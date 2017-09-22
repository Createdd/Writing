# Charting the Stock Market with React
[<img src="https://images.unsplash.com/photo-1504197618732-93c3d955d927?dpr=2&auto=format&fit=crop&w=1199&h=799&q=80&cs=tinysrgb&crop=">](
https://unsplash.com/photos/a6z2tYFEjR8)
Photo by peggy pardo on Unsplash - https://unsplash.com/photos/a6z2tYFEjR8

Once again I was working on an app from the [FreeCodeCamp curriculum](https://www.freecodecamp.org/challenges/chart-the-stock-market). In this article you can read the full documentation on the building process. 
Enjoy


## 📄 Table of contents

<!-- TOC -->

- [Charting the Stock Market with React](#charting-the-stock-market-with-react)
  - [📄 Table of contents](#📄-table-of-contents)
  - [The challenge](#the-challenge)
  - [Roadmap](#roadmap)
  - [Frontend](#frontend)
      - [Setup with the create-react-app package](#setup-with-the-create-react-app-package)
      - [React, Redux, React-vis](#react-redux-react-vis)
  - [Backend](#backend)
      - [Setting up the database (MongoDB hosted with Mlab)](#setting-up-the-database-mongodb-hosted-with-mlab)
      - [Routes](#routes)
      - [Adding Websocket](#adding-websocket)
  - [Adapt Frontend to the websocket](#adapt-frontend-to-the-websocket)
      - [Async actions in ducks/stocks.js (snippet):](#async-actions-in-ducksstocksjs-snippet)
      - [Collapsible Container - CollapsibleCon.js (snippet)](#collapsible-container---collapsibleconjs-snippet)
  - [Deploy to Heroku](#deploy-to-heroku)
  - [See the result](#see-the-result)

<!-- /TOC -->

---
>“Failure isn’t a necessary evil. In fact, it isn’t evil at all. It is a necessary consequence of doing something new.” 
― Ed Catmull
---

## The challenge 

See the full challenge [here](https://www.freecodecamp.org/challenges/chart-the-stock-market).

The user stories are pretty simple: 

- I can view a graph displaying the recent trend lines for each added stock.
- I can add new stocks by their symbol name.
- I can remove stocks.
- I can see changes in real-time when any other user adds or removes a stock. For this you will need to use Web Sockets.

It looks like this:

<img src="http://g.recordit.co/16EkuCTQSd.gif" alt="gif"/>

## Roadmap

I learned from [my last full-stack app](https://github.com/DDCreationStudios/Writing/blob/master/articles/LearningsFirstFullStack.md) that starting with the backend can induce some issues when you are working on the frontend later on. Therefore this time I will start with the frontend and finish with the backend.

1. Setup the environment with create-react-app
2. Lay out the basic React component structure
3. Set up the Redux eco system
4. Work over all components, divide them into container components and wire everything up with the Redux store
5. Build the Chart component with React-Vis
6. Build the backend using socket.io
7. Adapt the frontend to websockets
8. Deploy to Heroku

## Frontend

I will only highlight the key cornerstones and not provide a step-by-step tutorial.

#### Setup with the create-react-app package

This time I wanted to use [this boilerplate](https://github.com/facebookincubator/create-react-app) because I have used it many times before but never on a full-stack project. Although it has some limitations with the pre-configured structure, the benefits outweigh the problems by a mile. 

Basically it provides an environment, that: 

- React, JSX, ES6, and Flow syntax support.
- Language extras beyond ES6 like the object spread operator.
- A dev server that lints for common errors.
- Import CSS and image files directly from JavaScript.
- Autoprefixed CSS, so you don’t need -webkit or other prefixes.
- A build script to bundle JS, CSS, and images for production, with sourcemaps.
- An offline-first service worker and a web app manifest, meeting all the Progressive Web App criteria.

Pretty early actually I came to the point where I had to eject the configuration ( = opening the environment configuration for changes) to modify the webpack config. 

The problem was that I wanted to add jQuery for Materializecss and there always were some troubles. 
Solutions:
- Import jquery in ES6: https://stackoverflow.com/questions/37213647/es6-code-not-working-with-jquery
- Provide jquery plugin in webpack config: https://github.com/erikras/react-redux-universal-hot-example/issues/596

#### React, Redux, React-vis

This time I wanted to use [react-vis](https://github.com/uber/react-vis) for visualizing the chart. It is a visualization library based on D3 and developed by Uber. To summarize and quote their docs:

> A collection of react components to render common data visualization charts, such as line/area/bar charts, heat maps, scatterplots, contour plots, pie and donut charts, sunbursts, radar charts, parallel coordinates, and tree maps.

Some notable features:

- Simplicity. react-vis doesn't require any deep knowledge of data visualization libraries to start building your first visualizations.
- Flexibility. react-vis provides a set of basic building blocks for different charts. For instance, separate X and Y axis components. This provides a high level of control of chart layout for applications that need it.
- Ease of use. The library provides a set of defaults which can be overridden by the custom user's settings.
- Integration with React. react-vis supports the React's lifecycle and doesn't create unnecessary nodes.

Some practical issues I came across and solved were:

- Make react-vis chart responsive: https://github.com/uber/react-vis/issues/262
- To use gradients in react-vis properly, make sure tu include them in the Plot and adapt the reference points: http://uber.github.io/react-vis/#/documentation/general-principles/colors
- Use LineSeries instead of LineMarkSeries for better performance: http://uber.github.io/react-vis/#/documentation/series-reference/line-series

___
At this point the app was already pretty nice. Now I had to check the last User Story, which is to display real-life changes using a "web socket" backend.
___

## Backend


For the data I use the open API from [Quandl](https://www.quandl.com/). 


Server: index.js:

<script src="https://gist.github.com/DDCreationStudios/7c2daccf456b8c4c919a03cb21982cc1.js"></script>

___
```javascript
const express = require('express');
const morgan = require('morgan');
const path = require('path');
const app = express();
const server = require('http').Server(app);
const io = require('socket.io')(server);
const bodyParser = require('body-parser');
const mongoose = require('mongoose');
require('dotenv').config();

const stockModel = require('./dbModel');

server.listen(process.env.PORT || 9000);

app.use(morgan('dev'));
app.use(express.static(path.resolve(__dirname, '..', 'build')));
app.use(bodyParser.urlencoded({ extended: true }));
app.use(bodyParser.json());

//----DATABASE
var db = mongoose.connection.openUri(
	`mongodb://${process.env.REACT_APP_MONGO_USER}:${process.env
		.REACT_APP_MONGO_PASS}@ds125774.mlab.com:25774/chartstockmarket`
);
db.on('error', err => {
	console.log('FAILED to connect to mongoose');
	console.error(err);
});
db.once('open', () => {
	console.log('connected to mongoose');
});

//----Routes
app.get('/', (req, res) => {
	res.sendFile(path.resolve(__dirname, '..', 'build', 'index.html'));
});

app.get('/api/stocks', (req, res) => {
	stockModel.find({}, (err, stocks, next) => {
		if (err) return next(err);
		return res.status(200).json(stocks);
	});
});

//--------SOCKET
io.on('connection', function(socket) {
	console.log('New client connected with id:' + socket.id);
	socket.on('addStock', function(data) {
		var stockItem = new stockModel({
			stockName: data.toUpperCase()
		});
		stockItem.save((err, res) => {
			if (err) {
				console.log(err);
			} else {
				console.log(`Added new stock ${data.toUpperCase()}!`);
			}
		});
		socket.broadcast.emit('update', 'stockItem');
	});
	socket.on('removeStock', function(data) {
		stockModel.remove({ stockName: data }, (err, res) => {
			if (err) {
				console.log(err);
			} else {
				console.log(`Removed stock ${data}`);
			}
		});
		socket.broadcast.emit('removed', 'stockItem');
	});
	socket.on('disconnect', function() {
		console.log('Client disconnected');
	});
});

module.exports = server;
```
___


#### Setting up the database (MongoDB hosted with Mlab)

- Simply set up the [mlab]((https://mlab.com/)) account and a collection for the new app
- Create a mongoose model to simplify interactions with the database, like:

```javascript
const mongoose = require('mongoose');

var Schema = mongoose.Schema;

var stockSchema = new Schema({
  stockName: String
});

module.exports = mongoose.model('stockModel', stockSchema);
```

- Connect the express sever to the mlab

To solve the warning about the deprecated mongoose open connection, use openURI.

For more, see [here](http://mongoosejs.com/docs/connections.html).

#### Routes

- Set up a route the way that on default the production built index.html is consumed
- Set up another route to check the database for it's content and return it in the response

#### Adding Websocket

Use the Socket docs to set up listeners to:
- Display the connection
- Display a disconnection
- Save data to the database 
- Remove data from the database

Make sure to interact in the listener function with the mongoose model to harness the power of MongoDB.

---

On an additional note and because I spend literally 1 week on this issue:

Use `socket.BROADCAST.emit` to send the message to ALL sockets!!!

See more [here](https://stackoverflow.com/questions/9837998/socket-io-client-not-receiving-messages-from-server).

---

## Adapt Frontend to the websocket

The "problem" you have to overcome here is to render the components accordingly to the emitted actions of the socket. 

Key for these configurations are the handling in the component itself and in the ducks (Redux files).

I solved it by wiring up the container component with socket.io client and listening for changes. I did this with the `componentDidMount` lifecycle. Every time a message is emitted by the socket the component shall consult the database with dispatching actions to the Redux files. 

In the Redux files I fetch the data from the database and compare it with the current store of the application. Depending on this comparison the app fetches all data again from the Quandl service. This way every new socket client is able to check for themselves and always has the most up-to-date data.

Note, that I am not sure if this way is a good practice for a Redux/react application, since I handle much logic in the async action. Feel free to point out mistakes or misunderstood concepts! :)


#### Async actions in ducks/stocks.js (snippet):

```javascript
// Async actions with thunk
export function checkDB(stocks) {
	return dispatch =>
		axios
			.get('/api/stocks')
			.then(res => {
				if (stocks.length === 0) {
					res.data.map(elem => {
						dispatch(fetchStock(elem.stockName));
					});
				} else if (res.data.length < stocks.length) {
					dispatch(removeStock(stocks.length - 1));
				} else {
					let diff = [];
					res.data.map((item, i) => {
						if (i < stocks.length) {
							if (res.data[i].stockName !== stocks[i].dataset.dataset_code) {
								diff.push({
									stockName: item.stockName
								});
							}
						} else if (i === stocks.length) {
							diff.push({
								stockName: item.stockName
							});
						} else {
							diff = [];
						}
					});

					diff.map(elem => {
						dispatch(fetchStock(elem.stockName));
					});
					diff = [];
					// console.log(res);
				}
			})
			.catch(err => {
				console.warn(err);
			});
}

export function fetchStock(stockCode) {
	return dispatch =>
		axios
			.get(
				`https://www.quandl.com/api/v3/datasets/WIKI/${stockCode}.json?api_key=${process
					.env.REACT_APP_QUANDL_KEY}`
			)
			.then(res => {
				dispatch(addStock(res.data));
				// console.log(res.data);
			})
			.catch(err => {
				console.error(err);
				toastr['warning'](' ', 'Stock Code cannot be found!');
			});
}

export function newStock(stockCode, socket) {
	socket.emit('update', stockCode);
	return dispatch =>
		axios
			.get(
				`https://www.quandl.com/api/v3/datasets/WIKI/${stockCode}.json?api_key=${process
					.env.REACT_APP_QUANDL_KEY}`
			)
			.then(res => {
				dispatch(addStock(res.data));
				// console.log(res.data);
			})
			.then(socket.emit('addStock', stockCode))
			.catch(err => {
				console.error(err);
				toastr['warning'](' ', 'Stock Code cannot be found!');
			});
}

export function deleteStock(ind, stockCode) {
	const socket = socketIOClient('https://createdd-stockmarketchart.herokuapp.com/');
	socket.emit('removeStock', stockCode);
	return dispatch => {
		dispatch(removeStock(ind));
		console.log(`Deleted ${stockCode}`);
	};
}
```


#### Collapsible Container - CollapsibleCon.js (snippet)

<script src="https://gist.github.com/DDCreationStudios/1c6ac00b7b2f11fbf0f495f06425cb9b.js"></script>

```jsx
import React from 'react';
import PropTypes from 'prop-types';
import { connect } from 'react-redux';
import io from 'socket.io-client';

import Collapsible from './Collapsible';
import { checkDB, newStock, deleteStock } from '../../ducks/stocks';

export class CollapsibleCon extends React.Component {
	constructor(props) {
		super(props);
		const socket = io('https://createdd-stockmarketchart.herokuapp.com/');
		this.state = {
			value: '',
			response: '',
			lastAdd: '',
			socket: socket
		};
		this.addStock = this.addStock.bind(this);
		this.removeStock = this.removeStock.bind(this);
		this.handleChange = this.handleChange.bind(this);
	}
	componentWillMount() {
		this.props.checkDB(this.props.stocks);
	}

	componentDidMount() {
		this.state.socket.on('connect', () => {
			return console.warn('socket working! id: ' + this.state.socket.id);
		});
		this.state.socket.on('update', () => {
			this.props.checkDB(this.props.stocks);
		});
		this.state.socket.on('removed', () => {
			this.props.checkDB(this.props.stocks);
		});
	}
	handleChange(e) {
		this.setState({ value: e.target.value });
	}
	addStock(e) {
		e.preventDefault();
		this.props.newStock(this.state.value, this.state.socket);
		this.setState({ value: '' });
	}
	removeStock(ind, stockCode) {
		this.props.deleteStock(ind, stockCode);
	}
	render() {
		return (
			<div>
				<Collapsible
					stocks={this.props.stocks}
					addStock={this.addStock}
					removeStock={this.removeStock}
					onChange={this.handleChange}
					value={this.state.value}
				/>
			</div>
		);
	}
}
```

## Deploy to Heroku

For the deployment to Heroku it's import
- to use the create-react-app buildpack when using the webpack server
- to use the nodeJs buildpack when using your own websocket with your express server
- to set environment variables


## See the result

- See the live app [here](https://createdd-stockmarketchart.herokuapp.com/).
- See open source code [here.](https://github.com/DDCreationStudios/ChartTheStockMarket)
- See 5min timelapse [here.](https://www.youtube.com/watch?v=iPnyrrWJpLU)
- See 1hour relaxing coding session [here.](https://www.youtube.com/watch?v=8d6829bIxYg)



<img src="http://g.recordit.co/16EkuCTQSd.gif" alt="gif"/>

[![screenshot](../assets/STOCK/youtube.png)](https://www.youtube.com/watch?v=iPnyrrWJpLU)

Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
