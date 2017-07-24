# Intro to licensing open source projects

[<img src="https://images.unsplash.com/photo-1467664631004-58beab1ece0d?dpr=2&auto=format&fit=crop&w=767&h=511&q=80&cs=tinysrgb&crop=">](https://unsplash.com/photos/TTPMpLl_2lcA) https://unsplash.com/photos/TTPMpLl_2lc


A short introduction to licensing in open source. There are already many documents about licensing, however most of them are going to deep into the topic and confuse the reader. That's why I write a simplistic introduction with additional thoughts on more complex fields.


## 📄 Table of contents

<!-- TOC -->

- [Intro to licensing open source projects](#intro-to-licensing-open-source-projects)
  - [📄 Table of contents](#📄-table-of-contents)
  - [Before contributing](#before-contributing)
  - [Overview](#overview)
  - [Github's part in the equation](#githubs-part-in-the-equation)
    - [Open repositories and the (missing) license](#open-repositories-and-the-missing-license)
    - [Changes regarding licenses](#changes-regarding-licenses)
  - [Conclusion](#conclusion)
  - [Useful links & credits](#useful-links--credits)

<!-- /TOC -->

---

>"Personal liberty is not personal license." - Billy Sunday

---


## Before contributing

Before you write any code it's very beneficiary to rethink your goals for the project. Are you planning to write a small application just for yourself and feedback, or are you planning to build a large application with hundreds of contributors?
The bigger your application gets, the more important your thoughts about the best suitable license are!

As a core contributor or maintainer of the project be sure to acquire knowledge about licensing yourself. Since code projects can grow extremely quick over night be sure to address licensing better sooner than later.

When you are at a point where someone is making money with your project it is time to get some professional legal advice. Money spent in advance will help you tremendously with upcoming issues and gets you on the safe side.


## Overview

I hope many people know that platform, because I was really astonished when I saw it the first time. 

https://choosealicense.com/

This was the first site for the breaks down the complexity of licensing in easy understandable terms and provides an amazing overview.

<img src="../assets/LICENSE/choosealicense.png" alt="screenshot"/>

The home route instantly presents the most important licenses for the average developer. Those are the 

- MIT license (basically allows everything)
- Apache license 2.0 (you have to mark changes from the original and patents from the previous author are protected)
- GNU GPLv3 license (you are forced to use the same license and previous authors have more detailled patent/copyright protection)

Moving further on the page, they also provide a very good and precise overview over other licenses:

<img src="http://g.recordit.co/uXcCl0d4k4.gif" alt="gif"/>

The simplicity and structure makes it the perfect page for a first overview. 

However, there is a reason why licenses are formulated the way they are. Wording is key and very complex in legal aspects. So always make sure to really understand each of them in depth when using. Most of the pages provide links to the original terms. Use it ;)

>Note: "Open source licenses are licenses that comply with the Open Source Definition — in brief, they allow software to be freely used, modified, and shared. To be approved by the Open Source Initiative (also known as the OSI), a license must go through the Open Source Initiative's license review process."

## Github's part in the equation

Github does a lot to provide as much help as possible for developers to understand the legal aspects of open source.

They provide a [help page reagarding licensing your repository](https://help.github.com/articles/licensing-a-repository/) and even a [complete open source legal guide](https://opensource.guide/legal/).

### Open repositories and the (missing) license

First of all: 
>"Public repositories on GitHub are often used to share open source software. For your repository to truly be open source, you'll need to license it so that others are free to use, change, and distribute the software."

In my experience people seem not to be aware of the following. And I am here quoting their [page](https://help.github.com/articles/licensing-a-repository/):

>You're under no obligation to choose a license. However, without a license, the default copyright laws apply, meaning that you retain all rights to your source code and no one may reproduce, distribute, or create derivative works from your work. If you're creating an open source project, we strongly encourage you to include an open source license.

and

>If you want others to use, copy, modify, or contribute back to your project, you need to include an open source license. For example, someone cannot legally use any part of your GitHub project in their code, even if it’s public, unless you explicitly give them the right to do so.

>If you publish your source code in a public repository on GitHub, according to the Terms of Service, other GitHub users have the right to view and fork your repository within the GitHub site. If you have already created a public repository and no longer want users to have access to it, you can make your repository private. When you convert a public repository to a private repository, existing forks or local copies created by other users will still exist. For more information, see "Making a public repository private."

And also check the [Github terms of service](https://help.github.com/articles/github-terms-of-service/), which include:

>4. License Grant to Us ... That means you're giving us the right to do things like reproduce your content (so we can do things like copy it to our database and make backups); display it (so we can do things like show it to you and other users); modify it (so our server can do things like parse it into a search index); distribute it (so we can do things like share it with other users); and perform it (in case your content is something like music or video).

### Changes regarding licenses

Any change in licenses leads to 
- the requirement to rise awareness in the developer team and their working behaviour,
- increasing the complexity of the existing license structure, and
- consulting previous license holders and checking their scopes. 

In short: It demands much mure legal work. 


## Conclusion

So what does that all mean?
Simple: Know where you want to go with your project. Most copyright laws (depending on your country) see tight connections to publishing content. In many cases you lose a significant amount of rights after your intagible assets are made public. 

> Only publish code you are 100% sure you want it to be "open source" and be sure to do research (on law) if your project is getting bigger.

If you gained something from this article let me know with a comment or heart. Make sure to follow for more :)


## Useful links & credits
- [🌐 "Open Source Guide" - Github](https://opensource.guide/legal/)
- [📄 "Licensing a repository" - Github (article)](https://help.github.com/articles/licensing-a-repository/)
- [🌐 Open Source Initiative](https://opensource.org/licenses)

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
