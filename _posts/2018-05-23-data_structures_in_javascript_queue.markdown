---
layout: post
title:      "Data Structures in JavaScript: Queue"
date:       2018-05-23 17:16:19 -0400
permalink:  data_structures_in_javascript_queue
---


Just like a **stack**, a **queue** is a *linear data structure*. The difference is that whereas a stack utilizes **“last in, first out”** operations **(LIFO)**, a queue operates according to a **“first in, first out”** pattern **(FIFO)**. This is very much like a line at a deli, where the first customer in line gets served first.

![](https://i.imgur.com/inZdxwD.png)

**Basic Operations**

The basic operations of a queue are:

* **Enqueue** — places a new element at the back (or “tail”) of the queue
* **Dequeue** — retrieves the element at the queue’s front (or “head”)

**JavaScript Implementation**

Here is a simple implementation of a queue, utilizing a JavaScript class. We added a helper method `isEmpty()` to check if the queue is empty. 

![](https://i.imgur.com/n5houTs.png)

Now we can create our own queue, and enqueue/dequeue elements (in this case: dog names).

![](https://i.imgur.com/zL7njN8.png)

**Links**

[CS50: Queues](https://study.cs50.net/queues)

[Wikipedia: Queue (abstract data type)](https://en.wikipedia.org/wiki/Queue_(abstract_data_type))
