# Introducing TypeScript (with a section on JSX)

[<img src="https://images.unsplash.com/photo-1498309313100-e308c8946b45?dpr=2&auto=format&fit=crop&w=1080&h=1620&q=80&cs=tinysrgb&crop=">](
https://unsplash.com/photos/4Cjn0FDEud8)
Photo by 张 学欢 on Unsplash - https://unsplash.com/photos/4Cjn0FDEud8


Since I am getting more and more advanced, it was time to take a look into Typescript. Not because of the simple linting of JavaScript code, but rather because of the static typing concept.

In order to provide a certain standard of quality I mostly refer to and quote the following sources: 

- [The Github repository and wiki of Microsoft](https://github.com/Microsoft/TypeScript/wiki/TypeScript-Design-Goals)
(Licensed under [Apache License 2.0](https://github.com/Microsoft/TypeScript-Handbook/blob/master/LICENSE))
- [TypeScript DeepDive Gitbook by Basarat Ali Syed and it's contributors](https://basarat.gitbooks.io/typescript/docs/why-typescript.html)
(Licensed under [Creative Commons 4.0](https://creativecommons.org/licenses/by/4.0/))


## 📄 Table of contents

- [What is it and where is it heading?](#what-is-it-and-where-is-it-heading)
- [Concepts](#concepts)
    - [Basics Types](#basics-types)
    - [Interfaces](#interfaces)
    - [Generics](#generics)
    - [Intersections](#intersections)
- [React and JSX](#react-and-jsx)
    - [Setup](#setup)
    - [Concepts](#concepts-1)


---
> "Lack of documentation is becoming a problem for acceptance." - Wietse Venema

---

## What is it and where is it heading?

The idea behind TypeScript is to provide an optional type system for JavaScript. 

It enhances code quality by
- increase your agility when doing refactoring. It's better for the compiler to catch errors than to have things fail at runtime.
- types are one of the best forms of documentation you can have. The function signature is a theorem and the function body is the proof.

> Your JavaScript code .js file can be renamed to a .ts file and TypeScript will still give you back valid .js equivalent to the original JavaScript file. TypeScript is intentionally and strictly a superset of JavaScript with optional Type checking.

It's goals (according to the official documentation) are:
- Statically identify constructs that are likely to be errors.
- Provide a structuring mechanism for larger pieces of code.
- Impose no runtime overhead on emitted programs.
- Emit clean, idiomatic, recognizable JavaScript code.
- Produce a language that is composable and easy to reason about.
- Align with current and future ECMAScript proposals.
- Preserve runtime behavior of all JavaScript code.
- Avoid adding expression-level syntax.
- Use a consistent, fully erasable, structural type system.
- Be a cross-platform development tool.
- Do not cause substantial breaking changes from TypeScript 1.0.

## Concepts

___
> Essentially TypeScript is linting JavaScript. Just doing a better job at it than other linters that don't have type information.
___

#### Basics Types

Types are annotated using `:TypeAnnotation` syntax. (For example `var num: number = 123;`)

- Boolean (`let isDone: boolean = false;`)
- Number (`let decimal: number = 6;`)
- String (`let color: string = "blue";`)
- Array  (`let list: number[] = [1, 2, 3];` or `let list: Array<number> = [1, 2, 3];`)
- Tuple (`let x: [string, number]; x = ["hello", 10];`)
- Enum (`enum Color {Red, Green, Blue} let c: Color = Color.Green;`)
- Any (opt-out of type-checking and let some values pass through compile-time checks)
- Void (the absence of having any type at all)
- Null / Undefined (are subtypes of all other types. That means you can assign null and undefined to something like number)
- Never (is the return type for a function expression or an arrow function expression that always throws an exception or one that never returns)

#### Interfaces

Interfaces are the core way in TypeScript to compose multiple type annotations into a single named annotation.

```javascript 
interface Name {
    first: string;
    second: string;
}

var name: Name;
name = {
    first: 'John',
    second: 'Doe'
};
```

#### Generics

In languages like C# and Java, one of the main tools in the toolbox for creating reusable components is generics, that is, being able to create a component that can work over a variety of types rather than a single one. 

Without generics:
```javascript
function identity(arg: number): number {
    return arg;
}
```
While using any is certainly generic in that will accept any and all types for the type of arg, we actually are losing the information about what that type was when the function returns.


With generics:
```javascript
function identity<T>(arg: T): T {
    return arg;
}
```
T allows us to capture the type the user provides (e.g. number), so that we can use that information later.


#### Intersections

`extend` is a pattern in JavaScript where you take two objects and create a new one that has the features of both these objects.

Intersections allow to define those objects.

```javascript
function extend<T, U>(first: T, second: U): T & U {
    let result = <T & U> {};
//some code
    return result;
}
```

## React and JSX

#### Setup

Files that contain JSX have to end with `.tsx` instead of only `.ts` to be transpiled correctly.

Depending on the project setup you can enable three [JSX modes: preserve, react, and react-native](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/JSX.md#basic-usage).


#### Concepts

> React can either render HTML tags (strings) or React components (classes). The JavaScript emit for these elements is different (React.createElement('div') vs. React.createElement(MyComponent)). The way this is determined is by the case of the first letter. foo is treated as an HTML tag and Foo is treated as a component.

The fact that React renders strings or classes is essential for TypeScript. 

> In order to understand type checking with JSX, you must first understand the difference between intrinsic elements and value-based elements. Given a JSX expression `<expr />`, `expr` may either refer to something intrinsic to the environment (e.g. a div or span in a DOM environment) or to a custom component that you've created.

Intrinsic elements can be checked with interfaces, like 
```javascript
declare namespace JSX {
    interface IntrinsicElements {
        foo: any
    }
}

<foo />; // ok
<bar />; // error
```
Whereas value based elements are identified in their own scope, like

```javascript
import MyComponent from "./myComponent";

<MyComponent />; // ok
<SomeOtherComponent />; // error
```

Therefore, 
> Components are type checked based on the props property of the component.

For example:

```javascript
interface Props {
  foo: string;
}
class MyComponent extends React.Component<Props, {}> {
    render() {
        return <span>{this.props.foo}</span>
    }
}

<MyComponent foo="bar" />
```

Checking on attribute types on intrinsic elements is:

```javascript
declare namespace JSX {
  interface IntrinsicElements {
    foo: { bar?: boolean }
  }
}

// element attributes type for 'foo' is '{bar?: boolean}'
<foo bar />;
```

Whereas attributes on value based elements are checked like:

```javascript
declare namespace JSX {
  interface ElementAttributesProperty {
    props; // specify the property name to use
  }
}

class MyComponent {
  // specify the property on the element instance type
  props: {
    foo?: string;
  }
}

// element attributes type for 'MyComponent' is '{foo?: string}'
<MyComponent foo="bar" />
```


Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
