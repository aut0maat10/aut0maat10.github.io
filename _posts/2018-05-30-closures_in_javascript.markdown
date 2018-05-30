---
layout: post
title:      "Closures in JavaScript"
date:       2018-05-30 15:54:22 +0000
permalink:  closures_in_javascript
---


According to [YDKJS](https://github.com/getify/You-Dont-Know-JS), closure is everywhere in JavaScript, and you just need to learn to recognize it. 

[Closure is when a function can remember and access its lexical scope even when it's invoked outside its lexical scope.](https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20%26%20closures/ch5.md) 

In other words, a closure is an inner function that has access to an outer (enclosing) function's variables and scope chain.

**A closure has access to three scopes:**

1. Its own scope
2. The enclosing function's scope
3. The global scope

Here's an example from the [MDN docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures):

```
function init() {
  var name = 'Mozilla'; // name is a local variable created by init
  function displayName() { // displayName() is the inner function, a closure
    alert(name); // use variable declared in the parent function    
  }
  displayName();    
}
init(); // => alerts 'Mozilla'
```

**Closure Gotcha: `var` vs. `let`**

A common closure-related JS interview question is to guess the output of the following code:

```
for (var i = 1; i <= 5; i++) {
  setTimeout(function timer () {
    console.log(i);
  }, i * 1000);
}
```

One might be tempted to say that the output will be

```
1
2
3
4
5
```

at an interval of a second, but the output is actually

```
6
6
6
6
6
```

The problem is with the `setTimeout` call. You might hope that every `setTimeout` call would receive a new copy of `i`. However, the issue here is that `setTimeout` receives the value of` i` from its parent's scope. When you use `var` in the `for` loop, the variable becomes global, and after the time interval of 1000 milliseconds has passed, the loop has long finished and `i` rests steadily at 6.

With ES5, the solution was to use an [Immediatley Invoked Function Expression (IIFE)](https://developer.mozilla.org/en-US/docs/Glossary/IIFE). I won't get into that this time. Instead, the simple solution is to use` let` instead of `var`. 

The `let` statement (introduced with ES6) declares a block scope local variable, and passes the new value of i to every `setTimeout` call:

```
for (let i = 1; i <= 5; i++) {
  setTimeout(function timer () {
    console.log(i);
  }, i * 1000);
}
```

...and now we get the desired output:

```
1
2
3
4
5
```

**Links**

[You Don't Know JS: Scope & Closures](https://github.com/getify/You-Dont-Know-JS/tree/master/scope%20%26%20closures)

[MDN Docs: Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)






