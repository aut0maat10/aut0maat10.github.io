---
layout: post
title:      "Data Structures in JavaScript: Binary Search Trees"
date:       2018-06-13 19:20:47 +0000
permalink:  data_structures_in_javascript_binary_search_trees
---


This week, I'm going to do a quick implementation of a binary search tree in JavaScript. This first version features a simple `add `method in order to insert items into the data structure. I will look into other methods (search, delete...) some other time.

**Data Structures: Trees**

A **tree** is a data structure with a root node. Each node has child nodes. In a  **binary tree**, each node has at most two children. These children are referred to as *left child* and *right child*. This means that smaller values go to the left, and larger values go to the right (of the parent node).

![](https://upload.wikimedia.org/wikipedia/commons/d/da/Binary_search_tree.svg)

A **binary search tree** (BST) allows for fast lookup, addition, and removal of items. Binary search trees keep their keys in sorted order, so that lookup can use the principle of [binary search](http://electricsauna.net/binary_search). 

**Implementation**

Using [JS classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) to construct a `Node` and a `Tree`, a basic implementation with an `add` method would look like this:

```
class Tree {
  constructor() {
    this.root = null;
  }

  add(value) {
    // check if there is a root. if not, add new value as root.
    if (this.root === null) {
      this.root = new Node(value);
      break;
    }
    
    let current = this.root;
    
    while(true) {
      if (current.value > value) {
        // go left

        // if there is a left child, run loop again.
        if (current.left) {
          current = current.left;
        }
        // else, place the new node here (to the left of current node).
        else {
          current.left = new Node(value);
          break;
        }
      }
      else {
        // go right

        // if there is a right child, start again
        if (current.right) {
          current = current.right;
        }
        // else, place new node here.
        else {
          current.right = new Node(value);
          break; 
        }
      }
    }
  }
}


// Node class with default (null) values for left and right
class Node {
  constructor( value, left = null, right = null) {
    this.value = value;
    this.left = left;
    this.right = right;
  }
}
```

**Links:**

[Data Structures: Trees (HackerRank)](https://www.youtube.com/watch?v=oSWTXtMglKE)

[Algorithms (4th Edition): Binary Search Trees](https://algs4.cs.princeton.edu/32bst/)

[Wikipedia](https://en.wikipedia.org/wiki/Binary_search_tree)








