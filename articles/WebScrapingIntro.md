# Webscraping /-crawling with Javascript and Node.js

[<img src="https://images.unsplash.com/photo-1489747125620-900d12828f0d?dpr=2&auto=format&fit=crop&w=767&h=575&q=80&cs=tinysrgb&crop=&bg=">](https://images.unsplash.com/photo-1489747125620-900d12828f0d?dpr=2&auto=format&fit=crop&w=767&h=575&q=80&cs=tinysrgb&crop=&bg=)https://unsplash.com/photos/lOsbnJKTaI8

From the point I started to learn about web development I was enthusiastic about web crawling or web scraping. Most of the time it is called "web crawling", "web scrapping" or "web spider". Going through the web and using it's content for your ideas seems like an awesome idea to me. That's why I gathered some information and examples to provide an introduction to the topic.


## 📄 Table of contents


<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [Webscraping /-crawling with Javascript and Node.js](#webscraping-crawling-with-javascript-and-nodejs)
  * [📄 Table of contents](#table-of-contents)
  * [1. Frameworks and libraries](#1-frameworks-and-libraries)
  * [2. Examples](#2-examples)
  * [3. Scraping JavaScript rendered sites?](#3-scraping-javascript-rendered-sites)
  * [4. The legal side of web crawling](#4-the-legal-side-of-web-crawling)
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

That's a very good example of how easy it actually can get. I list these, because they are actually the most used ones in most of the tutorials available.

## 2. Examples

- Francis Kim explained in his [article](https://franciskim.co/promise-based-scraper-in-node-js/) how he scraped an certification website and automatically renders out an up-to-date list of developers. He uses **promises and mongodb**. It's amazing how he turns a callback based MongoDB native Node.js driver into a promise based one. Definitely check it out.


- Andrew Forth shows an alternative approach in his [article](https://www.sitepoint.com/web-crawling-node-phantomjs-horseman/). He combines Node.js with Phantom.js and Horseman. Node is able to use the headless WebKit **PhantomJS with the Horseman API**. He created a CLI micro-framework that crawls your github repositories as an example.


- Stephen from netinstructions.com reveals the sheer simplicity of web scrapting in his [article](http://www.netinstructions.com/simple-web-scraping-with-node-js-and-javascript/). He crawls Reddit, Hackernews and Buzzfeed.
His strategy is to identify the structure of the site he wants to crawl with the chrome devtools, grabs elements with **`cheerio` and then put the the scraped elements in a .txt file** together. In another [post](http://www.netinstructions.com/how-to-make-a-simple-web-crawler-in-javascript-and-node-js/) he also explains how to setup crawlers in Node.js.


- The article ["My open source Instagram bot got me 2,500 real followers"](https://medium.freecodecamp.com/my-open-source-instagram-bot-got-me-2-500-real-followers-for-5-in-server-costs-e40491358340) by TimG serves a great example for using **web crawling in Python with the Selenium framework** for real life purposes. Social media steadily gains importance in the marketing of businesses and using bots can be a valuable variable in executive decisions. His approach shows the effectiveness of simply programming. Definitely worth checking out!

## 3. Scraping JavaScript rendered sites?

The discussion about crawlabilty of JavaScript rendered websites reaches back many years and mostly discussed in terms of search engine optimization (SEO).
An easy answer for writing your own crawlers are HTML-rendering-engines that allow you to do the same as a normal browser.
Whereas there are many tools that allow you to meme such behavior, a practical example would be a [webdriver](http://webdriver.io/) used by [Selenium](http://www.seleniumhq.org/projects/webdriver/).



## 4. The legal side of web crawling

Web scrapping is an amazing way to gather much data with comparable low effort. Using and analyzing the collected data may provide advantages on a competition aspect und gives great insights on how a platform behaves.

#### Terms of use
First thing to look for are terms of use. Some Site explicitly address the possibility of using their website with scrapping APIs. Always be sure to take a look at these before.

#### Law in a wider sense

Copyright, privacy, competitive and civil law aspects may be violated depending on each case. It's important to see the difficulties between court rulings in different countries (especially America and Europe) and simply missing legislation caused by the fast progression of "internet cases".

It's safe to say that, if you have the feeling that some web scrapping actions are not legal, they probably aren't. Websites and, or databases often protected by simple intellectual property law. Which means that others are not allowed to use the data that is presented on the website.
This makes perfect sense because people put effort and knowledge into their online presentation and created data.

This extends to social media platforms in particular. Using their data and creating automated bots violate their fundamental principle of human interaction. It's therefore safe to assume that any kind of bots violate some applicable law.

This [article](https://www.bna.com/legal-issues-raised-by-the-use-of-web-crawling-and-scraping-tools-for-analytics-purposes) from 2013 shows the legal complexity in more detail.

They conclude:
>Ultimately, while the claims and theories that may be advanced in connection with the use of web crawling and scraping tools for analytics purposes have yet to be deeply explored by courts, this is likely a temporary state of affairs. Rather, given the increasing number and availability of tools for aggregation and analysis of content in the Big Data era, courts will ultimately be required to address these complicated issues.

Having that said, be prepared to face the consequences when site operators ban or sue you for infringing their principles.

## A list of established Node.js crawlers on Github

- [spider by Mikeal](https://github.com/mikeal/spider)
- [node-simplecrawler by cgiffard](https://github.com/cgiffard/node-simplecrawler)
- [node-crawler by bda-research](https://github.com/bda-research/node-crawler)



##



####


<img src="https://images.unsplash.com/photo-1485609315582-cfffa02888e8?dpr=2&auto=format&fit=crop&w=767&h=511&q=80&cs=tinysrgb&crop=&bg=" alt="apps" height="200"/>
https://unsplash.com/photos/ywJPwawYR08

## Conclusion







## Useful links & credits
- [📄 "Scraping the web with node js" - scotch.io](https://scotch.io/tutorials/scraping-the-web-with-node-js)
- [📄 "Web Scraping / Web Crawling Pages with Node.js" - JonathanMH](https://jonathanmh.com/web-scraping-web-crawling-pages-with-node-js/)
- [📄 "Promise Based Scraper in Node.js" - Francis Kim](https://franciskim.co/promise-based-scraper-in-node-js/)
- [📄 "MongoDB For Beginners: Introduction And Installation" -  Jake Rocheleau](http://www.hongkiat.com/blog/webdev-with-mongodb-part1/)
- [📄 "Web Crawling with Node, PhantomJS and Horseman" - Andrew Forth](https://www.sitepoint.com/web-crawling-node-phantomjs-horseman/)
- [📄 "Simple web scraping with Node.js and Javascript" - Stephen from Netinstructions.com](http://www.netinstructions.com/simple-web-scraping-with-node-js-and-javascript/)
- [📄 "How to make a simple web crawler with Node.js and Javascript" - Stephen from Netinstructions.com"](http://www.netinstructions.com/how-to-make-a-simple-web-crawler-in-javascript-and-node-js/)
- [📄 "Legal issues raused by the use of web crawling tools" -  Bloomberg Law Reports ](https://www.bna.com/legal-issues-raised-by-the-use-of-web-crawling-and-scraping-tools-for-analytics-purposes)
- [📄 "My open source Instagram bot" - TimG ](https://medium.freecodecamp.com/my-open-source-instagram-bot-got-me-2-500-real-followers-for-5-in-server-costs-e40491358340)
- [📄 "Ultimate guide for scraping JavaScript rendered web pages" - Naren Aryan](https://impythonist.wordpress.com/2015/01/06/ultimate-guide-for-scraping-javascript-rendered-web-pages/)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Web crawler development tutorials" - PatentPages](https://potentpages.com/web-crawler-development/tutorials/nodejs/)

```
If you gained something from this article let me know as a comment or heart. Make sure to follow for more :)
```

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
