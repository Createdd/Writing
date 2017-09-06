# Overview on Jest and Enzyme 
[<img src="https://images.unsplash.com/photo-1461023058943-07fcbe16d735?dpr=2&auto=format&fit=crop&w=1080&h=721&q=80&cs=tinysrgb&crop=">](
https://unsplash.com/photos/L-sm1B4L1Ns)
Photo by Demi DeHerrera on Unsplash - https://unsplash.com/photos/L-sm1B4L1Ns


## 📄 Table of contents

<!-- TOC -->

- [Overview on Jest and Enzyme](#overview-on-jest-and-enzyme)
  - [📄 Table of contents](#📄-table-of-contents)
  - [Jest API](#jest-api)
      - [Testing methods](#testing-methods)
      - [Snapshot Testing](#snapshot-testing)
  - [Enzymes methods](#enzymes-methods)
      - [Shallow rendering](#shallow-rendering)
      - [Full rendering](#full-rendering)
      - [Static rendering](#static-rendering)
      - [Selectors](#selectors)
      - [When testing](#when-testing)

<!-- /TOC -->

---
>"Testing leads to failure, and failure leads to understanding." - Burt Rutan
---

## Jest API

One of the reasons Jest gets more and more popular is the straight-forward and easy API.

#### Testing methods

Their global /  expect / matcher methods are:

|Global|Expect|Other matchers|
|---|---|---|
|[![screenshot](../assets/TESTREACT/globals.png)](https://facebook.github.io/jest/docs/en/api.html#methods)|[![screenshot](../assets/TESTREACT/expect.png)](https://facebook.github.io/jest/docs/en/api.html#methods)|[![screenshot](../assets/TESTREACT/matcherMethods.png)](https://facebook.github.io/jest/docs/en/api.html#methods)|

#### Snapshot Testing

Is used when you want to make sure that the UI does not change unexpectedly. 

From the [docs](https://facebook.github.io/jest/docs/en/snapshot-testing.html):

> A typical snapshot test case for a mobile app renders a UI component, takes a screenshot, then compares it to a reference image stored alongside the test. The test will fail if the two images do not match: either the change is unexpected, or the screenshot needs to be updated to the new version of the UI component.


> Snapshot testing is only one of more than 20 assertions that ship with Jest. The aim of snapshot testing is not to replace existing unit tests, but providing additional value and making testing painless. In some scenarios, snapshot testing can potentially remove the need for unit testing for a particular set of functionalities (e.g. React components), but they can work together as well.


## Enzymes methods

#### Shallow rendering

This is used to test the component on it's own. Isolated from other components. This is especially useful for testing representational or "dumb" React components.

From the [docs](http://airbnb.io/enzyme/docs/api/shallow.html):
> Shallow rendering is useful to constrain yourself to testing a component as a unit, and to ensure that your tests aren't indirectly asserting on behavior of child components.

#### Full rendering

Allows you to test whole DOM trees and gives you access to lifecycle methods in tests. 

#### Static rendering

Analyzes the resulting HTML structure. 

#### Selectors

Enzyme comes with a variety of great selectors. 

It allows for selecting

- CSS Selectors
  - class syntax (.foo, .foo-bar, etc.)
  - tag syntax (input, div, span, etc.)
  - id syntax (#foo, #foo-bar, etc.)
  - prop syntax ([htmlFor="foo"], [bar], [baz=1], etc.);
- React component constructors
- React component displayName
- Object Property Selector

#### When testing 

As Ambroise Laurent states in his [article](https://www.theodo.fr/blog/2017/04/enzyme-fast-and-simple-react-testing/):
> As a rule of thumb, shallow render is for unit testing and will probably be used for the majority of your test cases. Mounting would be more for a form of ‘front-end integration testing’ (seeing how a change in one component propagates to other components lower in the DOM tree). 


Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
