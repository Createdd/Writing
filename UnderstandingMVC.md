# 🛠 📐📏 Understanding MVC Architecture with React

[<img src="https://images.unsplash.com/photo-1484504844383-7676f295d034?dpr=2&auto=format&fit=crop&w=767&h=431&q=80&cs=tinysrgb&crop=">](https://unsplash.com/search/architecture?photo=b6GavtrLBo4)

Model-View-Controller (MVC) is a very often used software design pattern for implementing user interfaces. Since I tried to use and understand the structure in my last projects, I decided to take a deeper look into it. I want to focus on the model in the React environment.

---

>"If you can't understand it, you can't change it"
― [Eric Evans, Technologist](https://en.wikipedia.org/wiki/Domain-driven_design)

---

### What is MVC?
MVC is a way of thinking to structure your web application. It's popular because it's used by many frameworks that implement that structure (rails, cakephp, django etc.).
The architecture stems from the traditional flow of a web application.

<img src="http://i.imgur.com/fPHzoBY.png" align="right" height="300">
1. **View - Client**
Displays visualization of the data to the user. Only connected to the controller.
2. **Controller - Server**
Processes server-side logic and acts as a middleware between View and Model, i.e. controlling the flow of data.
3. **Model - Database**
Processing data from or to the database. Only connected to the controller.

See a practical example [here ➡️](https://www.tutorialspoint.com/design_pattern/mvc_pattern.htm)

### What are it's advantages and disadvantages for coding?
The structure allows flexibility since responsibilities are clearly separated. This leads to
- better and easier code maintenance and reusability
- easier to coordinate in teams due to the separation
- ability to provide multiple views
- support for asynchronous implementations

, but also to
- an increased complex setup process
- dependencies, i.e. changes in the model or controller affect the whole entity

### Implementing it into React
#### What
#### What


```
Please leave comments, feedback and suggestions as I am always trying to improve.
Share your thoughts - it's never been easier 😄
```


### Dive deeper - some useful links
- [🔀"Model-View-Controller" - Microsoft (retired content!)](https://msdn.microsoft.com/en-us/library/ff649643.aspx)
- [🔀"What is programming MVC" - DevMarketer (video)](https://www.youtube.com/watch?v=1IsL6g2ixak)
- [🔀"MVC Pattern" - Tutorialspoint (practical example)](https://www.tutorialspoint.com/design_pattern/mvc_pattern.htm)
- [🔀"Benefits of Using MVC Model" - Soroosh Pardaz (LinkedIn article)](https://www.linkedin.com/pulse/six-benefits-using-mvc-model-effective-web-soroosh-pardaz)
- [🔀"Model" - Microsoft]()
- [🔀"Model" - Microsoft]()
- [🔀"Model" - Microsoft]()
