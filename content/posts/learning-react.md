---
title: "Learning React"
date: 2021-11-26T14:07:37-04:00
draft: false
---


I am attempting to build a dApp. The problem is I do not know modern javascript, nor solidity. I am learning react as I build the product to ensure that I can hit my overall goal for building foreveraward.com

### Import curly braces

This question is asked on stackoverflow with a [great answer](https://stackoverflow.com/questions/36795819/when-should-i-use-curly-braces-for-es6-import)

Specifically, if I have a statement with the following:

```
import { A } from './A'
```

*This is a named import called A and only works if there is a named export called A*

```
export const A = 42
```

A module can only have one default export, but as many named exports as you'd like (zero, one, two, or many). You can import them all together:

```
// B.js
import A, { myA, Something } from './A'
```


### State

State has primarly was used with classes, but now with State Hooks since React 16.8 - it let's the developer use state and other react features without a class.

Basing log off of [here](https://reactjs.org/docs/state-and-lifecycle.html)

State also has lifecycles, and this is used in classes. There are some methods ment to be overridden for mounting and unmounting a component.
These are known as lifecycle methods
```
componentDidMount() {
}

componentWillUnmount() {
}
```

There are two Class methods that will mount (load the component) and unload the component

`this.state` is how state is managed in classes.
`setState(updater, [callback])`

setState() enqueues changes to the component state and tells React that this component and its children need to be re-rendered with the updated state. This is the primary method you use to update the user interface in response to event handlers and server responses.



### Arrow functions 

* In short, with arrow functions there are No binding of `this`
* the `this` keyword *always* represents the object that defined the arrow function


in regular methods the `this` keyword could represent the calling method, like the button in a form, this inside the method could represent that, while in an arrow function `this` represents the object that create the arrow function.

### Promise 

A Promise object is simply a wrapper around a value that may or may not be known when the object is instantiated and provides a method for handling the value after it is known (also known as resolved) or is unavailable for a failure reason (we'll refer to this as rejected).