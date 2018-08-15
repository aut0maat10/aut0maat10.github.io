---
layout: post
title:      "React Class Constructor: super() vs. super(props) – What's the Difference?"
date:       2018-08-15 19:21:35 +0000
permalink:  react_class_constructor_super_vs_super_props_whats_the_difference
---

![](https://i.imgur.com/ZCHzVeu.png)

If you initialize state and/or bind events in your React component, you need to have a `constructor()`. The constructor for a React component is called before the component is mounted. According to the [React docs](https://reactjs.org/docs/react-component.html#constructor), constructors typically only have two purposes:

> * Initializing local state by assigning an object to this.state.
> * Binding event handler methods to an instance.

Additionally, the React docs state that if you need to use a constructor, you should call `super(props)` before any other statement. There seems to be a lot of confusion regarding when and why you should pass `props` to `super()`, so I decided to find out how it works.

```
class someComponent extends React.Component {
  constructor(props) {
    super(); // or super(props) ?
  }
}
```

The simple reason is that if you need to access `props` within your constructor, you need to pass ` props` to `super()`. Consider these examples:

Example 1:

```
class someComponent extends React.Component {    
    constructor(props) {
        super(props)

        console.log(this.props) // => here, we have access to this.props!
    }
		
		// ...
}
```

Example 2:

```
class someComponent extends React.Component {    
    constructor(props) {
        super()

        console.log(this.props) // -> undefined
    }
		
		// ...
}
```

So, if you implement a constructor for a React component, you should call `super(props)` before any other statement in order to avoid bugs, and specifically pass in `props` if you need access to `this.props` within the constructor. 

It's also worth noting that calling `super()` with or without props has no effect on later use of `this.props` outside of the constructor, which means that for instance `render()` always has access to `this.props`.

**Links:**

[React Docs](https://reactjs.org/docs/react-component.html#constructor)

[Stack Overflow: Difference Between super() and super(props)](https://stackoverflow.com/questions/30571875/whats-the-difference-between-super-and-superprops-in-react-when-using-e)



