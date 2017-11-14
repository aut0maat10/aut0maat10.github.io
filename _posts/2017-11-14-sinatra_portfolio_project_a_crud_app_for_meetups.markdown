---
layout: post
title:      "Sinatra Portfolio Project: A CRUD App for Meetups"
date:       2017-11-14 18:16:11 +0000
permalink:  sinatra_portfolio_project_a_crud_app_for_meetups
---


The **Sinatra Portfolio Project** is my second bigger project for the **Online Web Developer** program at the **Flatiron School**. The main idea is to build a **CRUD** (Create, Read, Update, Delete) using **Sinatra**. The requirements are as follows: 

1. Build an **MVC Sinatra Application**.
2. Use **ActiveRecord** with Sinatra.
3. Use multiple models.
4. Use at least one **has_many** relationship.
5. Must have user accounts. The user that created a given piece of content should be the only person who can modify that content.
6. Must have the ability to create, read, update, and destroy the resource that belongs to a user and only that user is able to edit it.
7. You should also have validations for user input to ensure that bad data isn’t added to the database. The fields in your signup form should be required and the user attribute that is used to log in a user should be a unique value in the DB before creating the user.

![](https://i.imgur.com/Qw6Il52.png)

## Plan Twice, Code Once? 

I decided to build a simple app similar to [meetup.com](https://www.meetup.com/) , where users can create, join, update and delete meetups. I learned my lesson from the [CLI Gem Project](http://electricsauna.net/2017/09/30/cli_data_gem_project_-_scraping_tech_articles_on_google_news/), so this time, I spent a good portion of time planning the task at hand before I started coding. 

I used the [Corneal gem](http://thebrianemory.github.io/corneal/) to get started. **Corneal** is a Sinatra app generator that uses a file structure similar to what you would see in Rails, and comes loaded with useful gems, such as Sinatra, ActiveRecord, **SQLite3, Shotgun, Pry, Tux**, and **BCrypt**. 

## Migrations and Models

After installing Corneal, it was time to create some migrations and models. 

![](https://imgur.com/pOXEXiz)

For a simple version of a meetup app, I needed three tables to store meetups, RSVPs, and users, respectively. The RSVPs table would serve as a join table in order to connect users to meetups, and vice versa. In the corresponding models, a user has many RSVPs and many meetups through RSVPs, while a meetup also has many RSVPs and many users through RSVPs. An RSVP belongs both to a user and a meetup. 

![](https://i.imgur.com/pOXEXiz.png)

## User Login and Validation

After my migrations were in place, I spent some time playing around with Tux to see how the tables are connected in ActiveRecord and the database. Next, I created a users controller and got started on user login. I created signup, login, and logout routes in the controller, complete with corresponding views. I used sessions and helper class with **#is_logged_in?** and **#current_user** methods to keep track of the logged in user. I also secured the user’s password with BCrypt. 

## Meetups Controller
![](https://i.imgur.com/U5X59U5.png)

Next up was the meetups controller. Here I created some routes and corresponding forms to enable the user to create, edit, join, and delete meetups. I spent quite some time using Pry to work out how to connect the user to a meetup, and even more time on how to ensure that a user can only edit and delete a meet up they have created. I added a **creator_id** row to the RSVPs table to keep track of which user created a meetup, and ran into some trouble before I realized that I need to delete all RSVPs relating to a meetup when a user deletes a meetup (which in retrospect seems obvious, but took me a while to debug at the time). 

After some testing with multiple users, I did some light styling with **Bootstrap** in order to make the interface a bit more user friendly. And, we have a working app for meetups!

![](https://i.imgur.com/Dc9MqXk.png)

## Conclusion

There are obviously tons of improvements that could be made, but I had fun figuring out how to build this bare-bones version of a meetup app. I was particularly happy to notice that my skills have greatly improved since the first portfolio project, the CLI Gem. Sure, I ran into some problems along the way, but unlike the first time around, the challenges never felt overwhelming or impossible. It’s easier to find relevant information (thanks **Google**), and I’m also getting more comfortable with the Ruby docs and other technical documentation.

### Links:

[Github Repo](https://github.com/aut0maat10/meetup-app)

[Video walkthrough on Youtube](https://www.youtube.com/watch?v=KN4ImTpXNtI&t=12s)


### Screenshots:

![](https://i.imgur.com/a0xorK3.png)

![](https://i.imgur.com/0dfghml.png)

![](https://i.imgur.com/f8iTezv.png)










