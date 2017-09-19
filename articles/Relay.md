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

#### Containers and fragments

**Containers** are high-order components. They check if the data is available and update the component when the required data has been updated.

**Fragments** allow to compose components to queries. The are used by containers to define its own data requirements by creating a list of fragments (Note, that container can also use fragments defined by other containers!).

From the [learnrelay.org section](https://www.learnrelay.org/queries/containers-fragments#creating-a-relay-container):

```jsx
//index.js
const ViewerQueries = { viewer: () => Relay.QL`query { viewer }` }
<Route path='/' component={ListPage} queries={ViewerQueries} />

//A new Relay container is created and injects the prop 'viewer' to the ListPage component.
// A fragment on top of the viewer object defined in ViewerQueries is built
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
#### Variables

> Using query variables in this situation can increase code quality and performance, as string building is quite a costly operation.

From the [learnrelay.org section](https://www.learnrelay.org/queries/variables):
```javascript
//Initially, we sort descending by id and thus only query the first 100 Pokemons. If however the sortOrder variable is changed from within the component with a call to setVariables, we might change that amount to 1000.

export default Relay.createContainer(
  ListPage,
  {
    initialVariables: {
      sortOrder: 'id_DESC'
    },
    prepareVariables: (prevVariables) => ({
      amount: prevVariables.sortOrder.startsWith('id') ? 100 : 1000
    }),
    fragments: {
      viewer: () => Relay.QL`
        fragment on Viewer {
          allPokemons (first: $amount, orderBy: $sortOrder) {
            edges {
              node {
                ${PokemonPreview.getFragment('pokemon')}
                id
                name
                url
              }
            }
          }
        }
      `,
    },
  },
)
```

## Connections

Connections are relations between models. Relations between models or nodes are called 'edges' in Relay.


```javascript
//This will return a list of edges that all contain the id, name and url of every pokemon node in the allPokemons connection.
query {
  viewer {
    allPokemons (first: 1000) {
      edges {
        node {
          id
          name
          url
        }
      }
    }
  }
}
```


## Routes

> Routes are normal objects that declare root queries. Relay will aggregate the defined queries with fragments by using Relay.Renderer and send them to a remote server to fetch data.

```jsx
//Relay.Renderer will extract the fragment from the ListPage container and combine it with the pokemonRoute. Relay now knows where the starting node is and which data it needs to fetch. It will then send a request to a remote server and put the returned data in the specified store.
const pokemonRoute = {
  queries: {
    viewer: () => Relay.QL`
      query { viewer(first: $limit) }
    `
  },
  params: {
    limit: '1000'
  },
  name: 'PokemonRoute'
}

<Relay.Renderer
  Container={ListPage}                 // Relay Container
  queryConfig={pokemonRoute}           // Our route that we defined previously
  environment={Relay.Store}            // Default Relay store
/>
```

#### React Router

```jsx
<Router                                         // Router is a root component
  environment={Relay.Store}                     // Use the default Relay store to keep our data
  render={applyRouterMiddleware(useRelay)}      // Tell React Router to use Relay routing system
  history={browserHistory}                      // Use Browser History
>
  <Route                                        // Setup a path for the home page
    path='/'
    component={HomePage}
    queries={ViewerQueries}
  />
</Router>
```

## Mutations

Modifying or deleting data in the store is called mutation. Mutations consist of two steps: writing data to the store and reading all changed data from the store.

#### Methods

- getMutation() (to specify a name of a GraphQL mutation that we want to use)
- getVariables() (to prepare data that will be sent as input arguments in the GraphQL mutation)
- getFatQuery() (to specify all fields in our Relay Store that could have changed due to the mutation)
- getConfigs() (to tell Relay how to deal with the response data)

#### Relay Store

> Relay Store is a class that has two static methods for dispatching a mutation to the remote server, similar to calling an "Action" in Redux.

- commitUpdate() (to dispatch our mutation to the server)
- applyUpdate() (similar to commitUpdate but returns a transaction object to the mutation)

#### Types

Relay employs a client-side cache, which means that whenever a mutation is sent to the server, Relay needs to know how to update the cache with the mutation query result. Hence it's necessary to add mutation types to the `getConfigs` array.

Those types can be:
- RANGE_ADD (for creating a new node)
- FIELDS_CHANGE (for updating existing nodes)
- NODE_DELETE (for deleting a node)
- RANGE_DELETE (for deleting edges between nodes)
- REQUIRED_CHILDREN (for targeting fields that are not reachable, for example when a redirect to a newly created node is desired - rare cases)

#### Optimistic updates
Allows to define a desired server response. 

> In practice, optimistic updates improve the user experience by providing quick positive feedback to the user for a comparatively low trade off of occasionally misinforming the user of a successful action when really some kind of error occurred.

> To specify the optimistic response for a mutation, you can use the `getOptimisticResponse` method. The optimistic response acts as a mock payload and should only contain fields that you also included in your `fat query`, or `viewer`.



## Useful links & credits
- [📄 "Begin"](afgafgadgads)
- [📄 "learnrelay" on Github](https://github.com/learnrelay/learnrelay) under [MIT](https://github.com/learnrelay/learnrelay/blob/master/LICENSE)
- [📄 "React + Relay Tutorial"](https://www.howtographql.com/react-relay/0-introduction/)



Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
