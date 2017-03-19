# Start with C# and .NET

[<img src="https://images.unsplash.com/photo-1485856407642-7f9ba0268b51?dpr=2&auto=format&fit=crop&w=767&h=511&q=80&cs=tinysrgb&crop=">](https://unsplash.com/photos/ZMraoOybTLQ) https://unsplash.com/photos/ZMraoOybTLQ

Coming from a javascript world I wanted to get familiar with C# and it's NET environment. Since the gap between those 2 languages seemed huge to me, I decided to write a short introduction. To understand this introduction though, you have to have a little knowledge of programming fundamentals and core concepts.


## 📄 Table of contents

<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [Start with C# and .NET](#start-with-c-and-net)
  * [📄 Table of contents](#table-of-contents)
  * [1. What is C#?](#1-what-is-c)
  * [2. Notes on some C# keywords](#2-notes-on-some-c-keywords)
      * [Syntax](#syntax)
      * [Data types](#data-types)
      * [Type conversion](#type-conversion)
      * [Variables, constants and operators](#variables-constants-and-operators)
      * [Arrays and strings](#arrays-and-strings)
      * [Structures and classes](#structures-and-classes)
      * [Polymorphism, inheritance and encapsulation](#polymorphism-inheritance-and-encapsulation)
      * [Operator Overloading](#operator-overloading)
      * [Interfaces](#interfaces)
      * [Namespaces and "using"](#namespaces-and-using)
      * [Preprocessor directives](#preprocessor-directives)
  * [3. The .NET (Core) environment](#3-the-net-core-environment)
  * [Conclusion](#conclusion)
  * [Useful links & credits](#useful-links-credits)

<!-- tocstop -->




---

>"To be a good professional engineer, always start to study late for exams. Because it teaches you how to manage time and tackle emergencies." - Bill Gates

---


## 1. What is C#?
Microsoft define it themselves:
>C# is an elegant and type-safe object-oriented language that enables developers to build a variety of secure and robust applications that run on the .NET Framework. You can use C# to create Windows client applications, XML Web services, distributed components, client-server applications, database applications, and much, much more. Visual C# provides an advanced code editor, convenient user interface designers, integrated debugger, and many other tools to make it easier to develop applications based on the C# language and the .NET Framework.

C# syntax provides some features like:
- nullable value types ( types, to which you can assign normal range of values as well as null values)
- enumerations (a special sets of named values which all maps to a set of numbers)
- delegates (a reference type variable that holds the reference to a method)
- lambda expressions (an anonymous function that you can use to create delegates or expression tree types)
- direct memory access#



## 2. Notes on some C# keywords

#### Syntax
C# is an **object-oriented language**, which means that a program consists of various objects that interact with each other by means of actions.
Actions that are used by objects are called **methods**. Objects of the same kind are said to be in the same **class**.
A simple program includes namespaces and classes, which are in it's widest sense objects that interact with each other.

#### Data types
These types are categorized into:
- Value types, whom can be assigned a value directly
- Reference types, that store a reference like objects, dynamics or strings
- Pointer types, which store the memory address of another type

#### Type conversion
Is converting one type of data to another type (also known as Type Casting). In C#, type casting can be implicit or explicit. Whereas explicit type conversion is done by using a pre-defined function, implicit type conversion relies on using the same type environment (e.g. from smaller to larger integral types).

#### Variables, constants and operators
These don't really differ much from other languages. In C# they are categorized into different types. There is a lot content on the internet with a full list of types [(example)](http://www.techotopia.com/index.php/C_Sharp_Variables_and_Constants#C.23_Integer_Variable_Types).

A variable is a name for a storage area that the program can manipulate.

Constants are treated like regular variables except that their values cannot be modified after their definition.

An operator tells the compiler to perform specific mathematical or logical manipulations.

#### Arrays and strings
An array stores a fixed-size sequential collection of elements of the same type. An array is used to store a collection of data, but it is often more useful to think of an array as a collection of variables of the same type stored at contiguous memory locations.

Strings are an array of characters. Most of time the string keyword is used to declare a string variable - it's an alias for the System.String class.

#### Structures and classes

Microsoft provides an excellent [definition of structs and classes](https://msdn.microsoft.com/en-us/library/ms173109.aspx):

>A class is a reference type. When an object of the class is created, the variable to which the object is assigned holds only a reference to that memory. When the object reference is assigned to a new variable, the new variable refers to the original object. Changes made through one variable are reflected in the other variable because they both refer to the same data.

>A struct is a value type. When a struct is created, the variable to which the struct is assigned holds the struct's actual data. When the struct is assigned to a new variable, it is copied. The new variable and the original variable therefore contain two separate copies of the same data. Changes made to one copy do not affect the other copy.

>In general, classes are used to model more complex behavior, or data that is intended to be modified after a class object is created. Structs are best suited for small data structures that contain primarily data that is not intended to be modified after the struct is created.

#### Polymorphism, inheritance and encapsulation

>Inheritance, together with encapsulation and polymorphism, is one of the three primary characteristics (or pillars) of object-oriented programming.

Inheritance allows you to create new classes that reuse, extend, and modify the behavior that is defined in other classes.

The object-oriented principle of Encapsulation helps avoid duplicate relationships between information, allowing you to hide internal state and abstract access to it though type members such as methods, properties, and indexers.
> ▶️ Encapsulation helps you reduce coupling between objects and increases the maintainability of your code.

Polymorphism allows you to invoke derived class methods through a base class reference during run-time. This is handy when you need to assign a group of objects to an array and then invoke each of their methods.

Well that sounds super complicated? Check out this [amazing article](https://www.codeproject.com/Articles/602141/Polymorphism-in-NET), that explains it sooo well :)

#### Operator Overloading
> In an object oriented programming language like C#, operator overloading provides a much more natural way of implementing the operations on custom types. Suppose that we have a class created for Complex number and we want to perform all the arithmetic operations on this type. One way to do this is by having functions like Add, Subtract inside the class and have the functionality. Another way is to actually have the overloaded version of operators to act on this type.

#### Interfaces


>An interface is defined as a syntactical contract that all the classes inheriting the interface should follow. The interface defines the 'what' part of the syntactical contract and the deriving classes define the 'how' part of the syntactical contract.

Interfaces contain only the declaration of the members and define properties, methods and events.
The deriving class defines the members themselves accordingly to the laid out interface.
In essence interfaces provide a standard structure that the deriving classes would follow.

#### Namespaces and "using"

Are used
-  to organize the .NET framework's classes
-  to help control the scope of class and method names in larger programming projects

Namespaces are accessed through the keyword `using`.
>Most C# applications begin with a section of `using` directives. The section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.

#### Preprocessor directives

They instruct the compiler to preprocess the information before actual compilation starts.

All preprocessor directives begin with # and, since they are not statements, they do not end with a semicolon (;).

In a real time environment, the preprocessor directives are very helpful to set conditional compilation like setting up of default parameters based on the defined symbol, and prompting developers in terms of building project, and making conditional warnings and errors, etc.

Check out the [list](https://msdn.microsoft.com/en-us/library/ed8yd1ha.aspx) of preprocessor directives to get a feeling what they can do.


<img src="https://images.unsplash.com/36/IAG5tj7gThy5rOupZ5FK_IMG_3906.jpg?dpr=2&auto=format&fit=crop&w=767&h=511&q=80&cs=tinysrgb&crop=" alt="apps" height="200"/>
https://unsplash.com/photos/o2KD7JtqTlk

## 3. The .NET (Core) environment
I will focus on ASP.NET Core, since it's the newest redesign of ASP.NET and regarded as the future of the framework.

Microsoft defines it as:
>ASP.NET Core is a new open-source and cross-platform framework for building modern cloud based internet connected applications, such as web apps, IoT apps and mobile backends. ASP.NET Core apps can run on .NET Core or on the full .NET Framework. It was architected to provide an optimized development framework for apps that are deployed to the cloud or run on-premises. It consists of modular components with minimal overhead, so you retain flexibility while constructing your solutions. You can develop and run your ASP.NET Core apps cross-platform on Windows, Mac and Linux. ASP.NET Core is open source at GitHub.

Take time to read this paragraph well, since this official definition already answers many questions beforehand.

<img src="https://www.codeproject.com/KB/dotnet/1126303/image001.png" alt="MSDN Microsoft" height="200"/>
Source: https://blogs.msdn.microsoft.com

Radu Madei concluded in his [article](https://radu-matei.github.io/blog/dot-net-core-introduction/):
>It is one of the most exciting times to be a .NET developer, being able to write code that runs across IoT devices, phones, tablets, laptops, desktops, holographic devices, servers or the cloud and share it across multiple operating systems, with familiar processes and tools.

<img src="https://tl4blw.bn1301.livefilestore.com/y3m6sNWtdUd2Htc9yvtCL6sEvqjaJaEHh-2uGizu_fLU3hH7DL23-0nW104ESwTFZ32v6KmBeekCkZLmPQZIh6RklD-zE2vG4fi5Zo1mnqIR_gWugP1Es97QkxhK74JazU8NFgWomXCkbvgO7jZd5nxThPRrMGdCfwwc4THeX7eqU4?width=1280&height=720&cropmode=none" alt="MSDN Microsoft" height="200"/>
Source: https://radu-matei.github.io/blog/dot-net-core-introduction/

He also says:

>Basically, Microsoft built a version of .NET to allow developers to write cross-platform and cloud-optimized applications.

>First, .NET is cross-platform. It runs on Windows, macOS and Linux, which allows the developer to share and run the exact same code between machines running different operating systems, with no changes in code and minimum or no changes in the deveopment process. (Watch out for OS specific APIs!)

>But the true innovation in .NET came with the modularization in design and architecture. The compiler (Roslyn) and the runtime (CoreCLR) are separate components that allow you to use different implementations (or even write your own).

>Every library comes as a NuGet package, so when you start a new project, you don’t have any libraries, but a project file (currently a .json, in the future a .csproj to maintain consistency with all .NET projects) and a Program.cs. As you develop your app, you add libraries as you need them, allowing you to minimize the size of your application.

He sums up pretty well, what I was reading on different sites and various introductions. Check out [his article](https://radu-matei.github.io/blog/dot-net-core-introduction/) for more.









####


## Conclusion





## Useful links & credits
- [📄 "Introduction to C#" - Microsoft (article) ](https://msdn.microsoft.com/en-us/library/z1zx9t92.aspx)
- [🌐 "CSharp" - Tutorialspoint (guide)](https://www.tutorialspoint.com/csharp/index.htm)
- [🌐 "Csharp-station" provides articles, books, links, documentation and tutorials](http://csharp-station.com/)
- [📄 "Polymorphism in NET" - Manish Agrahari (article)](https://www.codeproject.com/Articles/602141/Polymorphism-in-NET)
- [📄 "Operator overloading" - Rahul Rajat Singh (article)](https://www.codeproject.com/Articles/452727/A-Beginners-Tutorial-on-Operator-Overloading-in-Cs)
- [📄 "Preprocessor directives in C#" Sridhar Patnayak (article)](https://www.codeproject.com/Articles/304175/Preprocessor-Directives-in-Csharp)
- [📄 "Begin"](https://docs.microsoft.com/en-us/aspnet/core/
)
- [🌐 "Introduction to ASP.NET Core" - Microsoft ](afgafgadgads)
- [📄 "Introduction to NET Core" - Pradeep Shet (article) ](https://www.codeproject.com/Articles/1126303/Introduction-to-NET-Core)
- [📄 ".NET Core Introduction" - Radu Matei (article)](https://radu-matei.github.io/blog/dot-net-core-introduction/)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
-

```
Please leave comments, feedback and suggestions as I am always trying to improve.
Share your thoughts - it's never been easier 😄
```

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
