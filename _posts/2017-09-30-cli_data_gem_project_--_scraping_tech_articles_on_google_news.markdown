---
layout: post
title:  "CLI Data Gem Project – Scraping Tech Articles on Google News"
date:   2017-09-30 13:48:53 -0400
---


For my first Flatiron School portfolio project (aka the CLI Data Gem Project) I built a news reader gem that scrapes Google News for technology-related articles, provides a list of articles, and allows the user to specify which article they would like to read.

**Tech Stack:** 

Ruby/Bundler
OpenURI
Nokogiri

![](https://imgur.com/WBT4hyE)

**Project Requirements**

1. Provide a CLI
2. CLI must provide access to data from a web page.
3. The data provided must go at least one level deep, generally by showing the user a list of available data and then being         able to drill down into a specific item.
4. Use good OO design patterns: you should be creating a collection of objects — not hashes

Setting up a Ruby gem was easy enough with bundler. The command

```
bundle gem tech_news
```

creates a scaffold directory for a new gem, and I named mine tech_news. Bundler 
also initializes a Git repository in this directory, which enables you to start committing 
right away. 

**Workflow: Simple to Complex**

My workflow was to start simple to get things running and add complexity and abstraction along the way. I started out creating the executable file tech-news in the bin, adding executable permissions and testing with a simple *“Hello World!”*

![](https://i.ytimg.com/vi/zecueq-mo4M/maxresdefault.jpg)

Next, I created a CLI class with a **#list_articles** method, a **#menu** method to ask for and deal with user input, a **#goodbye** method for when the user exits the program, and a **#call** method to bundle all these methods together. This method will then be called by the executable file tech-news to run the program. This structure keeps the executable file as clean as possible.  

**Hard Coding First**

First, I looked at the Technology section in Google News and copied a few article headlines and URLs, and hard-coded them into my CLI class in order to see how the modules and class methods interact, without worrying about web scraping at all at this point. I added methods and abstraction along the way, and found it useful to create an Article class to instantiate, save, and store articles, so that they could be called and listed by the CLI. When everything was working, it was time to plug in the real data by scraping the Technology section of Google News with **Nokogiri**. 

**Scraping with Nokogiri**

I created a class method **#scrape_google** to select an article’s headlines and urls on Google Technology News. This turned out to be not quite as easy as I had originally thought, but after selecting and iterating through the article XML elements and storing them in an array, I was able to select the attributes I wanted, i.e. the article title and the article url. With these attributes, I then iterated through the article array and created new instances of articles with the correct **@title** - and **@url** attributes for each article. All these new instances were then saved in the **#save** class method, accessible to the CLI through the **Article.all** method. 

![](https://imgur.com/DH1b5L2)

**It works! **

And there we have it — a working CLI news reader gem that selects and returns the latest Tech headlines from Google News, allows the user to enter a number that corresponds with the article they want to read, and the program returns the title and the URL of the article. This was a very interesting project, and I learned a lot about how Ruby modules and objects interact with each other. Moreover, I learned about the structure of Ruby Gems and CLIs, plus how to scrape the web with Nokogiri. 

**Improvements for Version 2.0**

Some possible improvements I would like to explore include adding the source/publisher of the individual article, perhaps an option to select related articles, and opening the selected article straight in the browser. 




