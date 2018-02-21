---
layout: post
title:      "React Refactoring: Separate Container from Presentational Component"
date:       2018-02-21 20:37:28 +0000
permalink:  react_refactoring_separate_container_from_presentational_component
---


In my React-Redux project, I had a component that would find and render a single item, like an item show page. In the first version, I had combined a stateful component with a `ItemShow` function in the same file:

![](https://i.imgur.com/TGeAZBv.png)

I wnated to separate the presentational function from the container component, according to [best practice guidelines](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0).  After some research, I found [this article in the React docs](https://reactjs.org/docs/state-and-lifecycle.html), which clearly explains how to convert a function (in my case, the `ItemShow` function) into a class.

As I'm new to React and Redux, with the `ItemShow` function still in place, I first experimented with the props a bit just to make sure everything was still working correctly:

![](https://i.imgur.com/FTtRv4N.png)

Then, following the React docs article, I broke the `ItemShow` function out of the container file and created a new file called `Item` with a new class concerned with presentation only:

![](https://i.imgur.com/jeCQOnL.png)

And finally, I let the container component render my new `Item` presentational component. Much cleaner!

![](https://i.imgur.com/n0tk7ck.png)

### Links:
[React Docs: State and Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)

[Fullstack React: Using Presentational and Container Components with Redux](https://www.fullstackreact.com/p/using-presentational-and-container-components-with-redux/)



