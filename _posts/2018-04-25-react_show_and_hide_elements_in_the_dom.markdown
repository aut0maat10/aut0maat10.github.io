---
layout: post
title:      "React: Show and Hide Elements in the DOM"
date:       2018-04-25 16:45:11 -0400
permalink:  react_show_and_hide_elements_in_the_dom
---


If you want to learn to play the guitar, reading about playing the instrument might be a good start, but in order to get good at it, you need hours and hours of practice and repetition. Programming is no different, so this week, I’ve been practicing my React skills by revisiting some tutorials.

One of the things I practiced this week is how to show and hide an element in the DOM with React. Sometimes you might want to hide an element and make it visible when you click a button, so that’s exactly what we’re going to do in this example.

I’m using [CodePen](https://codepen.io/), since it’s a great tool for practicing your coding skills. Check out the final React component [here](https://codepen.io/aut0maat10/pen/MGePJX). 

**Getting Started**

So, let's get started. After setting up the environment for React, we're going to add a simple `div` to the HTML section where our component will be displayed:

![](https://i.imgur.com/yY1UmwX.png)

Next, we create a simple React component with some basic information about a person. We set up the state of the component to store a person’s name, age, and address. Then, in the `render` function, we declare a `person` variable that formats the information stored in the state of the component. We wrap the information in a `div` with a class name of `personCard`. 

Next, we add a button which will be used to toggle the visibility of the element, and return the `person` variable (with some basic CSS styling). 

![](https://i.imgur.com/u8LWl2L.png)

This is the output so far:

![](https://i.imgur.com/I9WPO2l.png)

Of course nothing happens when we click the Toggle button, since we haven’t set up the click event yet. To get started with that, we will add a `showPerson` boolean to the state of the component and set it to `false` (because we want the person card to be hidden initially).

![](https://i.imgur.com/FTXsIdu.png)

**Add Click Handler**

Next, we are going to add the click handler on the button. We set up a `showPersonHandler` , which will be executed when the button is clicked:

![](https://i.imgur.com/zAJnIEW.png)

Now, we’re going to create the showPersonHandler. In this function, we store the state of our `showPerson` in a variable, let's call it ` isVisible`. Next, we are going to update the state to the opposite of the current boolean value of `isVisible`, using the [logical NOT operator](https://docs.microsoft.com/en-us/scripting/javascript/reference/logical-not-operator-decrement-exclpt-javascript).

**Wrapping Up**

One more thing: We need to add a conditional to our `render` function. First, we set our person variable to `null`. Then, we add an **if statement**. If `this.state.showPerson` is `true`, we want to show the element stored in our` person` variable in the DOM. Else, our person variable will be set to `null`, and nothing will be shown. 

And that’s it, we’re done! This is what our final component looks like:

![](https://i.imgur.com/ODrRIy2.png)

[Try it out on CodePen](https://codepen.io/aut0maat10/pen/MGePJX)









