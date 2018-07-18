---
layout: post
title:      "JS in the Browser: Local Storage vs Cookies"
date:       2018-07-18 22:40:58 +0000
permalink:  js_in_the_browser_local_storage_vs_cookies
---

![](https://i.imgur.com/kSU557h.jpg)

The purpose of this blog post is to explore the differences between cookies and local storage. 

An important difference between cookies and local storage is that cookies are primarily for reading server-side, while local storage can only be read by the client.

**Cookies**

* A small piece of data sent from the server, stored in the browser
* Designed as a mechanism to remember stateful information (e.g. items in a shopping cart, user’s browsing activity)
* Cookies have an expiration time
* Maximum storage value of 4KB
* The data is sent back to the server for every HTTP request, which increases the amount of traffic between client and server

**localStorage**

Part of the [Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API) (see also: [sessionStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage))
* Provides a mechanism in which browsers can store key/value pairs
* More intuitive than cookies
* Greater storage capacity (5MB) 
* The data is not sent back to the server for every HTTP request, which reduces the traffic between client and server
* Has no expiration date: the data stored in localStorage will persist until explicitly deleted
* Useful for saving user preferences

**Links**

[Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API)

[Stack Overflow](https://stackoverflow.com/questions/3220660/local-storage-vs-cookies)



