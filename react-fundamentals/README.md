# Fundamental of React Course Notes
[Found here](https://learn.tylermcginnis.com/);

## Introduction To Ecosystem

### Composition

  * Components manage their own state
  * Build a bunch of small components to build bigger Components
  * Encapsulate complexity into specific components, then put components together to build the interface

### Declarative

React is **mostly** declarative

  * Imperative = How
  * Declarative = What
  * Declarative Programming is programming with declarations, i.e. declarative sentences.

**Declarative Pros**

  * Reduce Side Effects - modifying state, making an API request
  * Minimise mutability
  * More readable code
  * Less bugs

### Unidirectional Data Flow

  * As the state updates the UI updates
  * Only worry about managing state and the app with will update the UI

### Explicit Mutations

  * Whenever the state updates, the UI updates.
  * whenever we call `setState()` we know the UI will updates


## React Pieces

  * **React Router** - Routing components
  * **Webpack** - code bundler
  * **Babel** - Code transformer. Transform JSX
  * **Axios** - HTTP requests

## Core concepts

### Pure functions

The whole concept of a pure function is **consistency** and **predictability**

* Pure functions always return the same result given the same arguments.
* Pure function's execution doesn't depend on the state of the application.
* Pure functions don't modify the variables outside of their scope.

React's **render** method needs to be a pure function


### Binding

'This' keyword

**Implicit Binding** - Left of the dot at Call Time
**Explicit Binding** - Call, apply, bind
**new Binding** - This is bound to the new object being constructed
**window Binding** -  defaults to window object if a function is invoked with 'this' and none of the above.

## Components

Component three fundamental parts:

* state
* Lifecyle events
* UI

### Lifecycle events

Reacts render method is a pure function, meaning in should not affect the state and only manage rendering to the UI.This includes setting props, making AJAX requests, adding and removing event listeners State should be managed outside using lifecycle methods.

Reacts lifecycle methods have two categories

* When a component gets mounted to the DOM and unmounted
* When a component receives data

#### Mounting/Un-mounting

**Setting props** - Use `deafultProps` to set default props
**Initial state** - Use ES6 constructor property. Use `this.setState` to pass in fn which return an obj that overwrites the State
**Ajax requests** - Use `componentDidMount`. Called directly after the component is mounted to the DOM
**Event Listeners** - For adding us same as above. For Removing us `componentwillUnmount`.

`shouldComponentUpdate` returns a boolean that will cause a re-render.

### Lifecyle Chart

![lifecycle](https://github.com/rossdowthwaite/tylermcginnis-courses/blob/master/react-fundamentals/react-lifecycle.png?raw=true)
