# Secrets of a JavaScript Ninja - book summary

[<img src="https://images.unsplash.com/photo-1476799460608-daf4ca3ef6c2?dpr=2&auto=format&fit=crop&w=767&h=510&q=80&cs=tinysrgb&crop=&bg=">](https://unsplash.com/photos/VDlG0OfIanU)https://unsplash.com/photos/VDlG0OfIanU


Here is a short summary and my takeaways from Resig, Bibeault, Maras book "Secrets of the JavaScript Ninja".  As an advanced beginner I was looking for a book that provides not only a great introduction, but also some in-depth content about JavaScript. The book exceeded my expectations - it simply was a great read. The Manning publications always provide great, high quality introductions to a topic with their well designed structure.

This summary contains some quotes from the book and is designed to provide an overview about what this book is about.

## 📄 Table of contents


<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [Secrets of a JavaScript Ninja - book summary](#secrets-of-a-javascript-ninja-book-summary)
  * [📄 Table of contents](#table-of-contents)
  * [1.JavaScript (JS) is everywhere](#1javascript-js-is-everywhere)
  * [2.Building the page at runtime](#2building-the-page-at-runtime)
  * [3.First-class functions: definitions and arguments](#3first-class-functions-definitions-and-arguments)
  * [4.Understanding function invocation](#4understanding-function-invocation)
  * [5.Closures and Scopes](#5closures-and-scopes)
  * [7.Object orientation with prototypes](#7object-orientation-with-prototypes)
  * [8.Controlling access to objects](#8controlling-access-to-objects)
  * [9.Dealing with collections](#9dealing-with-collections)
  * [10.Wrangling regular expressions](#10wrangling-regular-expressions)
  * [11.Code modularization](#11code-modularization)
  * [12.Working the DOM](#12working-the-dom)
  * [13.Surviving events](#13surviving-events)
  * [14.Developing cross-browser strategies](#14developing-cross-browser-strategies)
  * [Conclusion](#conclusion)
  * [Useful links & credits](#useful-links-credits)

<!-- tocstop -->


---

>"Physical comforts cannot subdue mental suffering, and if we look closely, we can see that those who have many possessions are not necessarily happy. In fact, being wealthy often brings even more anxiety." - Dalai Lama

---


## 1.JavaScript (JS) is everywhere
Understanding the foundations of client-side web applications will help you improve your development skills.
JS as a language is very functional oriented:
1. Functions are first-class objects - functions coexist with, and can be treated like any other JS object
2. Function closures - actively maintain („close over“) the external variables used in it’s body
3. Scopes - block level, global and function level variables
4. Prototype-based object orientation - instead of class-based object orientation, JS uses prototypes

This book focuses on core JS mechanisms such as functions, function closures, prototypes, generators, promises, proxies, maps, sets and modules.

## 2.Building the page at runtime
The HTML code received by the browser is used as a blueprint for creating the DOM, an internal representation of the structure of a client-side web application.
JavaScript is used to dynamically modify the DOM and bring dynamic behavior to web applications.
There are 2 phases for executing client-side web applications:
* Page building - HTML code is processed to create the DOM and global JS code is executed when script nodes are encountered.
* Evente handling - Various events are processed one at a time, relying on the event queue that stores events in the order they were executed. The event loop always checks for the top of the queue for events, and if an event is found, the matching event-handler function is invoked.

## 3.First-class functions: definitions and arguments
JS is a functional language and functions are first-class objects. Therefore they can be
* created via literals
* assigned to variables or properties
* passed as arguments
* returned as function results
* assigned properties and methods

Callback functions are functions that will be called later and is often used in event handling.Passing Properties to a function allows to store functions in functions to call later or to create a cache (memoization).
Types of functions are:
1. function declarations
2. function expressions
3. arrow functions
4. function generators

A parameter is a variable that is listed as part of a function definition, whereas an argument is value that is passed when invoking a function.
Rest parameters enable to reference the remaining arguments that don’t have matching parameter names.
Default parameters enable to specify default parameter values that will be used if no value is supplied during function invocation.

## 4.Understanding function invocation
Implicit parameters are this and arguments. The arguments parameter is a collection of arguments passed to the function. The  this parameter represents the function context, an object to which the function invocation is associated. How this is determined can depend on the way a function is defined as well as on how it’s invoked.

Functions can be invoked as:
* a function: skulk()
* a method: ninja.skulk()
* a constructor: new Ninja ()
* apply or call: skulk.apply(ninja) / skulk.call(ninja)

Function invocation and the value of this:
* Invoked as function: this is global window object (or undefined when using „strict mode“)
* Invoked as method: this is the object on which the function was invoked
* Invoked as constructor: this is the new constructed object
* Invoked with call or apply: this is the first argument supplied
* arrow functions inherit this from the function in which they are defined in

The bind method creates a new function. It has the same body, but it’s context is always bound to the passed in argument (a certain object), regardless of the way it’s invoked.

## 5.Closures and Scopes
Closures allow a function to access all variables that are in scope when the function itself was defined. It ensures that the function has all it needs even when the scope of creation is gone.
Closures are especially useful for:
* mimicking private object variables, by closing over constructor variables through method closures
* dealing with callbacks to simplify your code

JS engines track function execution through an execution stack and identifiers with lexical environments (scopes).
Variables can be globally-scoped, function-scoped and block-scoped:
* the var keyword defines a variable in the closest function or global scope
* let and const define a variable in the closest scope (including blocks)
* const allows to define variables whose values can be assigned only once

6.Generators and promises
Generators are functions that generate sequences of values - not all at once, but on a per request basis.
Unlike standard functions, generators can suspend and resume their execution. Within the body of a generator, the yield keyword yields a value and suspends the execution of the generator.
Calling a generator creates an iterator object through which we control the execution of the generator. New values are requested with the next method and exceptions are thrown with the throw method.

A promise is a placeholder for the results of a computation; most often asynchronous computation. A promise can either succeed or fail, and after it has done so, no more changes will be made.
Promises simplify the handling of asynchronous tasks significantly as interdependent asynchronous steps by using the then method to chain promises. The Promise.all method allows parallel handling of multiple asynchronous steps.

When combining promises and generators, asynchronous tasks can be handled elegantly with the simplicity of synchronous code.

## 7.Object orientation with prototypes
JS objects are simple collections of named properties with values.
Every object can have a reference to a prototype, an object to which a particular property is delegated, if the object itself doesn’t have the searched-for property. A prototype can have it’s own prototype, forming a prototype chain.
Prototypes are closely linked to constructor functions. A function’s prototype object has a constructor property pointing back to the function itself and this property is accessible to all objects instantiated with that function.

ES6 allows the class keyword that enables to mimic classes in JS (still based on prototype inheritance). The extends keyword enables elegant inheritance.

## 8.Controlling access to objects
Objects can be monitored with getters, setters and proxies.
Accessor properties can be defined by using get or set syntax as part of the object literal or ES6 classes.
A get method is implicitly called whenever a value is read, a set method is called whenever a value is assigned to the matching object’s property.
Getter methods are used for defining computed properties, whereas setter methods are used for data validation and logging.

Proxies are ES6 features that allow to control other objects in JS. They enable to define custom actions that will be executed when an object is interacted with. All interactions have to go through the proxy, which traps specific actions.
Proxies are used for logging, performance measurements, data validation, auto-populating object properties and negative array indexes.
Be aware that proxies are not fast and can effect performance.

## 9.Dealing with collections
Arrays are a special type of object with a length property and an Array.prototype as their prototype.
Common methods for modifying an array are:
* push and pop methods for adding and removing an item from the end of an array
* shift and unshift methods for adding and removing an item from the beginning of an array
* splice method for adding and removing an item from arbitrary array positions
* map method for calling a callback on every element and creating a new array
* every and some methods for determining whether items satisfy certain criterions
* find and filter methods for  finding items that satisfy certain conditions
* sort method for sorting an array
* reduce method aggregates all items in an array into one single value
Setting call or apply methods allow to reuse built-in array methods on objects.

Maps and dictionaries are objects that contain mappings between a key and a value.
Objects aren’t made for mapping because only string values can be used as keys and therefore running the risk of accessing prototype properties. Use the map collection instead.
Maps are collections that can be iterated over using a for…of loop.
Sets are collections of unique items.

## 10.Wrangling regular expressions
Regular Expressions trivialize the process of tearing apart strings and looking for information. Commonly they are used for:
* manipulating strings of HTML nodes
* locating partial selectors within a CSS selector expression
* determining whether an element has a specific class name
* input validation
ReEx can be created using literals (/test/) or the RegExp constructor ( new RegExp(„test“)).
Flags can be used to qualify your target:
* i for case-insensitive
* g for all instances of a pattern
* m for multiple lines
* y for sticky matching
* u for the use of Unicode escapes
Every string has access to the match function, which takes in a regular expression and returns an array containing the entire matched string along with any matched captures. The replace function, which causes a replacement on pattern matches rather than on a fixed string.

## 11.Code modularization
Modules are larger units of organizing code and allow to divide a program into more understandable , easier maintainable and improved reusable clusters of code.
Before ES6 modules has only been created by combining immediately invoked functions with closures. The immediate function created a new scope for defining variables and closures kept the variables alive from the outside. Two other module pattern are Asynchronous Module Definition (AMD)  and CommonJS.

ES6 modules combine the features of CommonJS and AMD:
* the modules are file based, i.e. one module per file
* import and export are identified with the import and export keyword
* a default export represents the whole module
* imports and exports can be renamed with the as keyword

## 12.Working the DOM
Converting an HTML string into DOM elements includes the following steps:
* the HTML string has to be valid HTML code
* wrap it into enclosing markup
* insert HTML into a DOM element
* extract the created DOM node
DOM attributes can be handled by getAttribute or setAttribute, DOM properties can be used with object property notation.
The style element property is an object that holds properties corresponding to the style values specified in the element markup.

## 13.Surviving events
Event-loop tasks represent an action performed by the browser. Tasks are grouped into two categories:
* Macrotasks are self-contained browser actions like creating the main document, handling events, and making URL changes
* Microtasks are smaller tasks, that are executed as soon as possible. For example promise callbacks and DOM mutation changes
JS works with a single-threaded execution model with at least two queues. (One for makrotasks and one for microtasks)
Timers can be used to break up computationally expensive code into manageable chunks.

An event that occurs on an element is usually propagated through the DOM. There are two propagation mechanisms:
* In event capturing, the event goes down from the top element to the target element
* In event bubbling, the event goes up from the target element to the top element
When calling event handlers, the browser passes in an event object. Elements can be accessed with the target property, and the  this keyword is used to refer to the element on which the action has been registered.
Dispatch with the dispatchEvent method to reduce compiling between different parts of your application.

## 14.Developing cross-browser strategies
Browsers aren’t bug-free and usually don’t support web standards consistently. Since it’s not possible to support all combinations, quality should never be sacrificed for coverage.
Cross-browser development involves:
* Code size - the smaller the better
* Performance Overhead - Keeping the performance level above a palatable minimum
* API quality - APIs should work across browsers

Techniques like feature detection with polyfills assure that the code is complete and protect against attacks from different directions.



<img src="https://images.unsplash.com/photo-1482682862782-8673966590d3?dpr=2&auto=format&fit=crop&w=767&h=511&q=80&cs=tinysrgb&crop=&bg=" alt="apps" height="200"/>
https://unsplash.com/photos/7WImcXVzyHk

## Conclusion

<a rel="nofollow" href="https://www.amazon.de/gp/product/1617292850/ref=as_li_tl?ie=UTF8&camp=1638&creative=6742&creativeASIN=1617292850&linkCode=as2&tag=ddcr-21"><img border="0" src="http://ws-eu.amazon-adsystem.com/widgets/q?_encoding=UTF8&ASIN=1617292850&Format=_SL110_&ID=AsinImage&MarketPlace=DE&ServiceVersion=20070822&WS=1&tag=ddcr-21" ></a><img src="http://ir-de.amazon-adsystem.com/e/ir?t=ddcr-21&l=as2&o=3&a=1617292850" width="200" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />


<img src="https://images-na.ssl-images-amazon.com/images/I/51UYwOhvQPL._SX395_BO1,204,203,200_.jpg" alt="apps" height="200"/>
https://unsplash.com/photos/7WImcXVzyHk




<a rel="nofollow" href="https://www.amazon.de/gp/product/1617292850/ref=as_li_tl?ie=UTF8&camp=1638&creative=6742&creativeASIN=1617292850&linkCode=as2&tag=ddcr-21">Secrets of the JavaScript Ninja, Second Edition</a><img src="http://ir-de.amazon-adsystem.com/e/ir?t=ddcr-21&l=as2&o=3&a=1617292850" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />


## Useful links & credits
- [📖 "Secrets of the JavaScript Ninja, Second Edition"](https://www.amazon.de/gp/product/1617292850/ref=as_li_tl?ie=UTF8&camp=1638&creative=6742&creativeASIN=1617292850&linkCode=as2&tag=ddcr-21)

```
If you gained something from this article let me know as a comment or heart. Make sure to follow for more :)
```

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
