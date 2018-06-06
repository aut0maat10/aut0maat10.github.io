---
layout: post
title:      "Data Structures in JavaScript: Linked List"
date:       2018-06-06 22:55:40 +0000
permalink:  data_structures_in_javascript_linked_list
---


**Linked Lists vs. Arrays**

Like the array, a linked list is a linear collection of data elements. While the elements in an array are stored contiguously in memory, a linked list is connected through pointers. Whereas arrays are static structures that can't easily be extended or reduced, linked lists are more dynamic. Each element (node)  in a linked list is a separate object. This allows for easier insertion and deletion.

![](https://upload.wikimedia.org/wikipedia/commons/1/17/LinkedList.jpg)

**Nodes**

A linked list node is a kind of struct with two parts:

* data of some data type
* a pointer to another node of the same type

The set of nodes together can be thought of as a chain of elements that can be followed from the beginning to the end.

A JavaScript implementation of a node might look like this:

```
class Node {
  constructor(value) {
    this.value = value;
    this.next = null; 
  }
}
```

We want to keep track of the length, head (start), and tail (end) of the list.

```
class LinkedList {
  constructor() {
    this.length = 0;
    this.head = null;
    this.tail = null;
  }
}
```

Next, let's implement a push function in order to add items to  the list. If there is no head (i.e. the list is empty), the node we add will be assigned as the new head. Else, the new node will be added to the tail of the list.

```
push(value) {
    const node = new Node(value);
    this.length++;
    if (!this.head) {
      this.head = node;
    }
    else {
      this.tail.next = node;
    }
    this.tail = node;
  }
```

Let's also implement a find method to search for a value in the list. We will start at the head, and as long as the pointer does not point at `null` (which means we have reached the end of the list), we will inspect every node in the list. If the value we search for is not in the list, we will return `null`. 

```
find(value) {
    let currentNode = this.head;
    while (currentNode) {
      if (currentNode.value === value) {
        return currentNode;
      }
      currentNode = currentNode.next;
    }
    return null;
  }
```

Finally, let's add a method to delete an element at a specific index. As a linked list is really about pointers, we need to find the previous node to the node we are deleting. Next, we change the previous node's pointer to skip the node we want to delete, and make it point to the next one in line instead.

![](https://www.geeksforgeeks.org/wp-content/uploads/gq/2014/05/Linkedlist_deletion.png)

We also need to check if it is the `head` we want to delete (at index 0). If so, we make the next node the new head of the list. When `count` equals `index`, we break out of the while loop, and "skip" `currentNode` (to be deleted) by setting `previousNode.next` equal to `currentNode.next`.

```
remove(index) {
    let count = 0;
    let currentNode = this.head;
    let previousNode = null;

    if (index > this.length) return null;
    if (index === 0) {
      this.head = currentNode.next;
      this.length--;
      return this.head; 
    }    
    while(count < index) {
      previousNode = currentNode;
      currentNode = currentNode.next;
      count++;
    }
    previousNode.next = currentNode.next;
    currentNode = null;
    this.length--
    return this.head;
  }
```

Here is the full implementation, using two separate JS classes (Node + LinkedList):

```
class LinkedList {
  constructor() {
    this.length = 0;
    this.head = null;
    this.tail = null;
  }
  // add item to linked list
  push(value) {
    const node = new Node(value);
    this.length++;
    if (!this.head) {
      this.head = node;
    }
    else {
      this.tail.next = node;
    }
    this.tail = node;
  }
  // find a value in list
  find(value) {
    let currentNode = this.head;
    // go from node to node until we find our value
    while (currentNode) {
      if (currentNode.value === value) {
        return currentNode;
      }
      currentNode = currentNode.next;
    }
    // if value not found
    return null;
  }
  // remove a value at index
  remove(index) {
    let count = 0;
    let currentNode = this.head;
    let previousNode = null;

    if (index > this.length) return null;
    if (index === 0) {
      this.head = currentNode.next;
      this.length--;
      return this.head; 
    }    
    while(count < index) {
      previousNode = currentNode;
      currentNode = currentNode.next;
      count++;
    }
    previousNode.next = currentNode.next;
    currentNode = null;
    this.length--
    return this.head;
  }
}

// node class

class Node {
  constructor(value) {
    this.value = value;
    this.next = null; 
  }
}
```











