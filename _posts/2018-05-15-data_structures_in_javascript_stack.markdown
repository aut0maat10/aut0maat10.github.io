---
layout: post
title:      "Data Structures in JavaScript: Stack"
date:       2018-05-15 17:24:24 +0000
permalink:  data_structures_in_javascript_stack
---


![A stack of cafeteria trays](https://i.imgur.com/AbXAEN0.jpg)

In computer science, a *stack* is an abstract data type that serves as a collection of elements. A stack has **two principal operations**:

* **push** — adds an element to the top of the stack
* **pop** — removes the most recently added element

**Last In, First Out**

Because of the order of these operations, an alternative name for a stack is **LIFO (last in, first out)**.

It can be useful to think of a stack as a pile of cafeteria trays. When the cafeteria staff puts trays out before meals, they pile the trays from the bottom to the top, and when a customer grabs a tray, they remove the top one from the stack of trays. The last tray put on the the stack is the first one to be taken from the stack.

![](https://i.imgur.com/h3QQ5in.jpg)

A more practical example of a stack is the “undo” operation of a text editor. Every time text is added to a text editor, the most recent text is pushed to the top of the stack. When a user hits “undo”, the top of the stack (i.e. the most recent change) is removed from the stack. This process can be repeated until there is nothing left on the stack, which in this case would be a blank file.

**Implementation in JavaScript**

This is an example implementation of a stack using a JavaScript class:  

![](https://i.imgur.com/IlsCyjR.png)

**Example Usage:**

![](https://i.imgur.com/B4mbIUq.png)

**Non-essential Operations**

In addition to the essential operations of the stack (push, pop), some other common operations include:

* **peek** – return the element at the top of the stack without deleting it
* **size** – return the size of the stack
* **isEmpty** –– check if the stack is empty

**Stack Implementation with Added Operations:**

![](https://i.imgur.com/8S46DnZ.png)



