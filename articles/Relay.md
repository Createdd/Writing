# Introducing Relay
[<img src="https://images.unsplash.com/photo-1500004621732-74cd4ad4d53e?dpr=2&auto=format&fit=crop&w=1080&h=721&q=80&cs=tinysrgb&crop=">](
https://unsplash.com/photos/LCJ9iOli-uE)
Photo by gdtography on Unsplash - https://unsplash.com/photos/LCJ9iOli-uE

GraphQL is on the rise and so is the React inspired, data-driven framework Relay.



## 📄 Table of contents


---
>“However much you study, you cannot know without action. 
A donkey laden with books is neither an intellectual nor a wise man. 
Empty of essence, what learning has he whether upon him is firewood or book?” 
― Saadi
---

## The power

Quoting Facebook's [introduction article](https://facebook.github.io/react/blog/2015/02/20/introducing-relay-and-graphql.html): 

> The design enables even large teams to make changes with a high degree of isolation and confidence. Fetching data is hard, dealing with ever-changing data is hard, and performance is hard. Relay aims to reduce these problems to simple ones, moving the tricky bits into the framework and freeing you to concentrate on building your application.

> By co-locating the queries with the view code, the developer can reason about what a component is doing by looking at it in isolation; it's not necessary to consider the context where the component was rendered in order to understand it. Components can be moved anywhere in a render hierarchy without having to apply a cascade of modifications to parent components or to the server code which prepares the data payload.

> Relay provides a predictable environment for developers by maintaining an invariant: a component won't be rendered until all the data it requested is available. Additionally, queries are defined statically (ie. we can extract queries from a component tree before rendering) and the GraphQL schema provides an authoritative description of what queries are valid, so we can validate queries early and fail fast when the developer makes a mistake.

Relating to a FLUX architecture:

> In some ways Relay is inspired by Flux, but the mental model is much simpler. Instead of multiple stores, there is one central store that caches all GraphQL data. Instead of explicit subscriptions, the framework itself can track which data each component requests, and which components should be updated whenever the data change. Instead of actions, modifications take the form of mutations.





## The eco system

An application using Relay requires:
- A GraphQL Schema (description of a data model with associated methods to fetch data)
- A GraphQL Server ()
- Relay

In short:
>  React lets you build your UI declaratively, Relay lets you describe your data declaratively using GraphQL.

## Queries

To make a request to a server a query has to be sent. 
Data can be accessed by the identifier of an item (`node(id:$id)`) or by properties of a certain user (`viewer` object).

#### Containers

Containers are high-order components. They check if the data is available and update the component when the required data has been updated.

Quoting the [learnrelay.org section](https://www.learnrelay.org/queries/containers-fragments#creating-a-relay-container):

```javascript
//A new Relay container is created and injects the prop 'viewer' to the ListPage component.
export default Relay.createContainer(
  ListPage,
  {
    fragments: {
      viewer: () => Relay.QL`
        fragment on Viewer {
          id
        }
      `,
    },
  },
)
```






## Useful links & credits
- [📄 "Begin"](afgafgadgads)
- [📄 "React + Relay Tutorial"](https://www.howtographql.com/react-relay/0-introduction/)



Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
