---
layout: post
title:      "Creating a REST API with Node.js (Getting Started)"
date:       2018-06-20 21:23:24 +0000
permalink:  creating_a_rest_api_with_node_js_getting_started
---

![](https://cdn-images-1.medium.com/max/1600/1*wMZnVAEei1xbY1v6sAbYxQ.png)

During the past few weeks, I have been focusing on learning more about full stack JavaScript. I’m interested in the MERN stack (MongoDB, Express, React, Node.js), and as a company I’m interested in working for is using this particular stack, I decided to dive into some tutorials and create a RESTful API with Node.js. 

Since the MERN stack is very popular, there are some great tutorials out there. I can highly recommend [Creating a REST API with Node.js](https://www.youtube.com/watch?v=0oXYLzuucwE ) and [An Easy Way to Get Started with the MERN Stack](https://alligator.io/react/mern-stack-intro/) by [alligator.io](https://alligator.io/) , for instance.

**What is a RESTful API?**

**REST** stands for **REpresentational State Transfer**. It’s an architectural style that defines a set of constraints and properties based on HTTP.  It was first presented by **Roy Fielding** in 2000 in his famous [dissertation](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm). 

**REST** has six architectural constraints, which you can [read more about here](https://restfulapi.net/rest-architectural-constraints/).

**Getting Started**

I have Node installed, so I created a directory `node-restful-shop` , `cd` into it, and ran `npm init `to create a `package.json` file. Next, I installed [Express](https://expressjs.com/) with the command `npm install --save express`. 

Next, I created a simple  `server.js` file, in order to set up my Node server. 

![](https://i.imgur.com/u38BNjN.png)

After that, I added an `app.js` file and hooked it up with the bare-bones server.

![](https://i.imgur.com/qyPXoct.png)

After starting the server with node server.js, I opened up `localhost:3000` in the browser, just to check that everything works:

![](https://i.imgur.com/zXWmeYH.png)

Now that we have a very basic server running, it's time to add more routes, a database, and more. That, however, I'm going to save for my next blog post.



