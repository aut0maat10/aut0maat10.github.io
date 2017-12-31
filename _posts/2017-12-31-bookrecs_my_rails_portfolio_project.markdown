---
layout: post
title:      "BookRecs – My Rails Portfolio Project  "
date:       2017-12-31 13:47:32 -0500
permalink:  bookrecs_my_rails_portfolio_project
---


#### For my Rails Portfolio Project for the Flatiron School, I decided to build an app for book recommendations and reviews. The app is inspired by Goodreads, and I call it BookRecs. 

![](https://i.imgur.com/dKzLcay.png)

### Project Requirements:&#x2028;

* Use Rails framework
* Models must include a has_many, a belongs_to, and a has_many_through relationship
* Models should include reasonable validations
* Include at least one level ActiveRecord scope methods
* Include a nested form that writes to an associated model through a custom attribute writer
* Must provide standard user authentication (signup, login, logout, passwords)
* Your authentication system should allow login from some other service (Facebook, Google, Twitter…)
* Make use of a nested resource with the approveriate RESTful URLs
* Your forms should correctly display validation errors
* The application should be, within reason, a DRY Rails app
* Do not use scaffolding

I wanted users to be able to sign in/log in in order to create books and write reviews. The user is able to see the books on the index page, but must log in to create, edit, or delete books and reviews. For user authentication, I used the **Devise** gem. For login from an external service, I chose to let the user log in with **Google**, using [Omniauth with Google](https://github.com/zquestz/omniauth-google-oauth2#omniauth-google-oauth2-strategy).

Before coding , I spent a good deal of time planning my models and **ActiveRecord** associations. My basic associations (at the start of the project) looked like this:

![](https://i.imgur.com/FCRdihH.png)

### Create and Rate

With the migrations in place, got started by creating the books controller and a basic index page for the books. Then, I added a form to create books. Styling wasn’t a part of the requirements, but I wanted my app to look good, so with the help of [this YouTube tutorial](http://www.youtube.com/watch?v=AMai9EZesXY), I did some basic styling with [bootstrap-sass](http://rubygems.org/gems/bootstrap-sass/versions/3.3.7). I also added the [Paperclip gem](http://rubygems.org/gems/paperclip) in order to upload images of book covers, and later added [Raty](https://wbotelhos.com/raty) to display the ratings as stars. 

![Book show page with ratings and reviews](https://i.imgur.com/fqyZwJf.png)

I created a show page for the books, and also added functionality to edit, update, and destroy books. I also added a Bootstrap navbar with a dropdown menu to filter books by genre on the index page. By adding nested resources for genres and books, my app now displays all books of a particular genre (e.g. localhost:3000/genres/2/books). 

![Index page showing all books in the Fiction genre](https://i.imgur.com/k0eFfoB.png?1)

### User Authentication and Authorization

The hardest part was getting the Google OmniAuth to work properly with Devise, and I spent quite some time debugging and searching the web for answers. In the end,  [these instructions](https://www.digitalocean.com/community/tutorials/how-to-configure-devise-and-omniauth-for-your-rails-application) turned out to be useful, and now  the user can sign in to my app with their Google account.

![](https://i.imgur.com/IGZ9RPH.png)

Finally, I worked on user authorization, and made sure that you can only view and create books if you’re signed in. Moreover, I made sure that only the user that created the book can edit it and delete it. I also added the same features for reviews. This means that I had to tweak the associations between models a little bit, adding a user_id column to the books table. 

#### And finally, the first version of the BookRecs app is done! This was a fun project and a great introduction to working with Ruby on Rails. 

![](https://i.imgur.com/IOQ3Lqr.png)

### Links:

[GitHub Repo](https://github.com/aut0maat10/book_recs)

[Video Walkthrough](https://www.youtube.com/watch?v=7GCCK4m7SXk)









