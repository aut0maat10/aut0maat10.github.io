---
layout: post
title:      "Updating My Rails Project – Adding jQuery Features to BookRecs"
date:       2018-02-12 18:37:48 +0000
permalink:  updating_my_rails_project_adding_jquery_features_to_bookrecs
---


Feels like I'm only getting started, but I have already reached the Rails Project with a jQuery Frontend in the Flatiron School curriculum. The scope of this project is to add some jQuery functionality to an existing Rails project –  in my case, my BookRecs app. 

For my first Rails project, I built an app called BookRecs, where users can register to add, review, and recommend their favorite books. In order to work with JSON data, I first set up some Active Model Serializers for my project:  a Book has many Reviews, and a Review belongs to a Book. 

![](http://i.imgur.com/B4n4qQd.png)

On the Book show page, I implemented a "Next" button, in order to get the next book in the index through an AJAX request. This turned out to be a bit of a challenge, mainly since I allow the user to delete books, so the book ids in the array of books aren't necessarily incrementing by one every single time. 

Using the JSON data I received through the AJAX request, I saved instances of books in a JavaScript object, and then injected the book attributes into the proper divs with jQuery.  In my app, I use Raty to display star ratings for books, and I also spent some time figuring out how to plug in the correct values with jQery in order to display the ratings.

![](http://i.imgur.com/M0aZam5.png)

Next, I created another JavaScript object for a Review, and updated my form for reviews to add a review with AJAX and jQuery. Again, I struggled a bit trying to render the Raty stars correctly, but now you can submit a new review without a page refresh.

![](http://i.imgur.com/7J5mPDz.png)

Working on this project, I learned a lot about Active Model Serializers and AJAX requests. I am also interested in learning more about  `:remote => true` in Rails (which was off-limits in this particular project). In terms of rendering pages through AJAX, there are many improvements I would like to make for BookRecs, but those will have to wait until I graduate, which hopefully should be soon!

![](http://i.imgur.com/4bxwzx0.png)


Links: 

[GitHub Repo](https://github.com/aut0maat10/book_recs)

