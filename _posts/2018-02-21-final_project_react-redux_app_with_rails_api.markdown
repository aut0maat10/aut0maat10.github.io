---
layout: post
title:      "Final Project: React-Redux App with Rails API"
date:       2018-02-21 12:20:27 -0500
permalink:  final_project_react-redux_app_with_rails_api
---


Close to six months after starting the **Full Stack Web Developer Program** at the **Flatiron School**, I have finally reached the final project(!) Now it’s time to take everything I’ve learned over these past few months and somehow distill it into one big project, and “*demonstrate mastery of material in this course*”, as stated on the project page. Intimidating? Yes. Very.

The main requirements for the project include using a **Rails API** to handle the backend and persisting of data, and let **React** and **Redux** handle the frontend. The `create-react-app` generator should be used to set up the boilerplate app. Moreover, the code should be written in **ES6** as much as possible, there should be three routes (handled by `react-router`), and Redux middleware should be used to respond to and modify state change.

![](http://i.imgur.com/fniSFQ0.jpg)
 	
After a couple of days of ~~overestimating my React skills~~ planning, I realized that in order to truly understand how all these moving parts/libraries fit together, I need to scale down and build something very simple, adding functionality along the way. I decided to build a bare-bones marketplace app, where you can add items through a form, persist the items in the Rails API database, fetch the data with Redux actions, list all items in the React frontend, and render an individual item with all its information in an item-show view.

This would have been a fairly easy task in Rails, since I’ve grown reasonably comfortable navigating that particular framework by now. React, however, was pretty much unchartered waters to me, so I knew that would be the real challenge of this project.

I started out by setting up the backend. This was the first time running rails in API mode for me, so that was an interesting new experience. [This article](http://www.fullstackreact.com/articles/how-to-get-create-react-app-to-work-with-your-rails-api/) turned out to be very helpful. I set up `create-react-app` to work with the Rails API server, having the Webpack development server proxy requests intended for the API:

![](http://i.imgur.com/52dzxj9.png)

In order to run the app locally, you need to launch both the Webpack server and the API server. To handle this, I set up Foreman, which is a utility for handling multiple processes. All you need to do is declare the two processes in a Procfile, and then the client app will run on `localhost:3000` and the API will be listening on  `localhost:3001` . In order to boot [Foreman](http://github.com/ddollar/foreman), you just run `foreman start -p 3000`  . Even better, you can add a Rake task:

```
task :start do
  exec 'foreman start -p 3000'
end
```

...and boot the app with `rake start` .

The hardest part by far for me was figuring out the flow to properly fetch the data from the API, get it to the Redux store, and render it in the React view. I ended up using [axios](http://github.com/axios/axios) to wrap the fetch action, and was finally able to dispatch the data to the store. 

![Redux actions](https://i.imgur.com/HjfIOhf.png)

After ~~days~~ hours of trial and error, numerous tutorials and in-person consultations, and varying levels of frustration, I was eventually able to display a simple index list on the page:

![](http://i.imgur.com/xGR6qGg.png)

Encouraged by this monumental victory, I created a form for entering data and persisting it to the database. This turned out to be a far easier task, thanks to [Redux Form’s great documentation](http://redux-form.com/7.2.3/) . 

After some minor tweaking, I was able to get the form to submit and persist the data to the database, and redirect to the index page after submitting. Next, I created a simple navbar for orientation, and did some minor [styling with react-bootstrap](https://react-bootstrap.github.io/) . 

![](http://i.imgur.com/kjiK2TD.png)

This project was a nice introduction to React and Redux with a Rails backend. It took me a while to get even this far, but I feel like I gained a pretty solid understanding of the flow of React and Redux in the process. This is definitely a very basic 1.0 version of the project, and I’m looking forward to learning more about React in order to add more functionality, such as editing and deleting items, user authentication, and more.

### Links:

[Github Repo](https://github.com/aut0maat10/react-redux-project)

[Fullstack React: Using create-react-app with a Rails Server](https://www.fullstackreact.com/articles/how-to-get-create-react-app-to-work-with-your-rails-api/)

[React Docs](https://reactjs.org/)

[Redux Docs](https://redux.js.org/)

[Redux Form](https://redux-form.com/7.2.3/)


