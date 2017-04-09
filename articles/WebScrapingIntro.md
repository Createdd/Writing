# Introduction to Webscraping with Javascript and Node.js

[<img src="https://images.unsplash.com/photo-1489747125620-900d12828f0d?dpr=2&auto=format&fit=crop&w=767&h=575&q=80&cs=tinysrgb&crop=&bg=">](https://images.unsplash.com/photo-1489747125620-900d12828f0d?dpr=2&auto=format&fit=crop&w=767&h=575&q=80&cs=tinysrgb&crop=&bg=)https://unsplash.com/photos/lOsbnJKTaI8

From the point I started to learn about web development I was enthusiastic about web crawling or web scraping. Going through the web and using it's content for your ideas seems like an awesome idea to me. That's why I demonstrate the basics with an easy example.


## 📄 Table of contents


<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [Introduction to Webscraping with Javascript and Node.js](#introduction-to-webscraping-with-javascript-and-nodejs)
  * [📄 Table of contents](#table-of-contents)
  * [1. Frameworks and libraries](#1-frameworks-and-libraries)
  * [2. Examples](#2-examples)
  * [The legal side of web crawling](#the-legal-side-of-web-crawling)
      * [Terms of use](#terms-of-use)
      * [Law in a wider sense](#law-in-a-wider-sense)
  * [A list of established Node.js crawlers on Github](#a-list-of-established-nodejs-crawlers-on-github)
  * [Conclusion](#conclusion)
  * [Useful links & credits](#useful-links-credits)

<!-- tocstop -->


---

>"“If you decide that you’re going to do only the things you know are going to work, you’re going to leave a lot of opportunity on the table.”" - Jeff Bezos

---


## 1. Frameworks and libraries

In the [tutorial "Scraping the web with Node.js" ](https://scotch.io/tutorials/scraping-the-web-with-node-js) by Scotch.io following frameworks are used to simple traverse a film review website:

- NodeJS
- ExpressJS: minimal and flexible Node.js web application framework with features for web and mobile applications
- Request: Helps making HTTP calls
- Cheerio: Implementation of core jQuery specifically for the server (helps to traverse the DOM and extract data)

That's a very good example of how easy it actually can get. I also list these, because they are actually the most used ones in the tutorials available.

## 2. Examples

- Francis Kim explained in his [article](https://franciskim.co/promise-based-scraper-in-node-js/) how he scraped an certification website and automatically renders out an up-to-date list of developers. He uses **promises and mongodb**. It's amazing how he turns a callback based MongoDB native Node.js driver into a promise based one. Definitely check it out.

- Andrew Forth shows an alternative approach in his [article](https://www.sitepoint.com/web-crawling-node-phantomjs-horseman/). He combines Node.js with Phantom.js and Horseman. Node is able to use the headless WebKit **PhantomJS with the Horseman API**. He created a CLI micro-framework that crawls your github repositories as an example.

- Stephen from netinstructions.com reveals the sheer simplicity of web scrapting in his [article](http://www.netinstructions.com/simple-web-scraping-with-node-js-and-javascript/). He crawls Reddit, Hackernews and Buzzfeed.
His strategy is to identify the structure of the site he wants to crawl with the chrome devtools, grabs elements with **`cheerio` and then put the the scraped elements in a .txt file** together. In another [post](http://www.netinstructions.com/how-to-make-a-simple-web-crawler-in-javascript-and-node-js/) he also explains how to setup crawlers in Node.js.

## The legal side of web crawling

Web scrapping is an amazing way to gather much data with comparable low effort. Using and analyzing the collected data may provide advantages on a competition aspect und gives great insights on how a platform behaves.

#### Terms of use
First thing to look for are terms of use. Some Site explicitly address the possibility of using their website with scrapping APIs. Always be sure to take a look at these before.

#### Law in a wider sense

Copyright, privacy, competitive and civil law aspects may be violated depending on each case. It's important to see the difficulties between court rulings in different countries (especially America and Europe) and simply missing legislation caused by the fast progression of "internet cases".

In my opinion it's safe to say that, if you have the feeling that some web scrapping actions are not legal, it probably isn't. Websites and, or databases often protected by simple intellectual property law. It means that others are not allowed to use the data that is presented on the website.
This makes perfect sense because people put effort and knowledge into their online presentation and created data.

This

## A list of established Node.js crawlers on Github

- [spider by Mikeal](https://github.com/mikeal/spider)
- [node-simplecrawler by cgiffard](https://github.com/cgiffard/node-simplecrawler)
- [node-crawler by bda-research](https://github.com/bda-research/node-crawler)



##



####


<img src="https://images.unsplash.com/photo-1485609315582-cfffa02888e8?dpr=2&auto=format&fit=crop&w=767&h=511&q=80&cs=tinysrgb&crop=&bg=" alt="apps" height="200"/>
https://unsplash.com/photos/ywJPwawYR08

## Conclusion

Web Crawling with Node, PhantomJS and Horseman





## Useful links & credits
- [📄 "Scraping the web with node js" - scotch.io](https://scotch.io/tutorials/scraping-the-web-with-node-js)
- [📄 "Web Scraping / Web Crawling Pages with Node.js" - JonathanMH](https://jonathanmh.com/web-scraping-web-crawling-pages-with-node-js/)
- [📄 "Promise Based Scraper in Node.js" - Francis Kim](https://franciskim.co/promise-based-scraper-in-node-js/)
- [📄 "MongoDB For Beginners: Introduction And Installation" -  Jake Rocheleau](http://www.hongkiat.com/blog/webdev-with-mongodb-part1/)
- [📄 "Web Crawling with Node, PhantomJS and Horseman" - Andrew Forth](https://www.sitepoint.com/web-crawling-node-phantomjs-horseman/)
- [📄 "Simple web scraping with Node.js and Javascript" - Stephen from Netinstructions.com](http://www.netinstructions.com/simple-web-scraping-with-node-js-and-javascript/)
- [📄 "How to make a simple web crawler with Node.js and Javascript" - Stephen from Netinstructions.com"](http://www.netinstructions.com/how-to-make-a-simple-web-crawler-in-javascript-and-node-js/)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
-

```
Please leave comments, feedback and suggestions as I am always trying to improve.
Share your thoughts - it's never been easier 😄
```

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
