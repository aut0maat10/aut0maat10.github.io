---
layout: post
title:      "Understanding the JavaScript Event Loop"
date:       2018-07-11 22:38:44 +0000
permalink:  understanding_the_javascript_event_loop
---


![](https://i.imgur.com/SKUJQaj.jpg)

JavaScript is a single-threaded language. Still, JavaScript is capable of asynchronous operations. Despite allowing asynchronous JS code, JavaScript itself never had any built-in notion of asynchronous behavior (at least not up until ES6). This means that every JS program is divided into chunks of code, and every chunk (e.g. function) gets executed one piece at a time. Tasks that cannot complete immediately —  Ajax requests, for instance — will be completed asynchronously. That’s why JS makes use of callback functions which will be executed at a later stage. 

Consider these two examples:

```
const data = $.get( "http://some-url" );
console.log( data );
// Oops! we probably won't get any data...
```

... but this will work: 

```
$.get( "http://some.url.1",  (data) => {
	console.log( data ); 
	// Yay, we have 'data'!
});
```


It’s important to note that the JS engine doesn’t run in isolation, but in a hosting environment. The most common hosting environments include the browser and the server (via Node.js).

What these hosting environments have in common is a mechanism that handles executing multiple chunks of JS code over time, at each moment invoking the JS engine. This mechanism is called the event loop.

When your program makes an Ajax request to fetch data from a server, you set up the response code in a callback function. This is the engine telling the hosting environment “hey I’m going to suspend execution for now, but when you have finished the GET request and have some data, please call this function back”. 

The browser is then set up to listen to a response from the network, and when it has some data, it schedules the callback function to be executed by inserting it into the event loop. 

Here is some simplified code (courtesy of [YDKJS](https://github.com/getify/You-Dont-Know-JS)) to illustrate the event loop: 

```
// `eventLoop` is an array that acts as a queue (first-in, first-out)
var eventLoop = [ ];
var event;

// keep going "forever"
while (true) {
	// perform a "tick"
	if (eventLoop.length > 0) {
		// get the next event in the queue
		event = eventLoop.shift();

		// now, execute the next event
		try {
			event();
		}
		catch (err) {
			reportError(err);
		}
	}
}
```

The event loop is a continuously running loop, and each iteration is called a “tick”. For each tick, if there is an event waiting on the queue, it will be taken off and executed. These are your function callbacks.

This means that if there are, say, 30 items in the event loop at the moment, your next callback gets in line behind the others. At any given moment, only one event can be processed at a time. If you’re not aware of how the event loop works, you might run into some unexpected behavior, such as this code: 

```
setTimeout(() => console.log('first'), 0)
console.log('second')

// => second
//=> first
```

**Links:**

[You Don't Know JS: Asynch & Performance](https://github.com/getify/You-Dont-Know-JS/blob/master/async%20%26%20performance/ch1.md)

[MDN Web Docs: Event Loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop)
