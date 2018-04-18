---
layout: post
title:      "Sorting Algorithms 3: Merge Sort"
date:       2018-04-18 19:02:59 +0000
permalink:  sorting_algorithms_3_merge_sort
---


*I recently graduated from Flatiron School’s Full Stack Web Development Online Program. After six months of programming in Ruby and Javascript, I have seen my main interest gradually shift from frontend to backend design. Consequently, as I am now entering the job search program, part of my daily routine is to focus on computer science, data structures, and algorithms. The purpose of this blog is to document and articulate the things I learn.*

**Merge sort** is a [divide and conquer algorithm](https://en.wikipedia.org/wiki/Divide_and_conquer_algorithm), and a very stable and consistent sorting algorithm. When you call `Array.prototype.sort` in JavaScript, it often uses merge sort (depending on the engine and the types of the elements in the array). 

A key to merge sort is that it is recursive, so you should probably have a good understanding of [recursion](https://docs.microsoft.com/en-us/scripting/javascript/advanced/recursion-javascript) before you try to implement merge sort.

**You can think of a divide and conquer algorithm as having three parts:**

1. Divide the problem into subproblems that are smaller instances of the same problem
2. Conquer the subproblems by solving them recursively
3. Combine the solutions to the subproblems into the solution for the original problem

**Pseudocode for Merge Sort**

1. Divide list in half until you have *n* sublists (an array with one element is considered sorted).
2. Compare each element with the adjacent list, sort and merge until all elements are sorted.

![](https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif)

In sorting a list of *n* elements, merge sort has an average and worst case performance of **O(n log n)**. 

**Implementation**

We are going to split the problem into two functions: **mergeSort** and **merge**. The mergeSort part basically just splits the list into smaller lists recursively, using a “left” and a “right” array: 

![](https://i.imgur.com/tOQ7jUz.png)

Then, we’re going to stitch it all together with the merge function. We'll keep doing a loop while there still are elements in the left and right arrays. We are comparing the first elements in the left and right arrays, pushing the smaller number into an array called **result**. At the end, you will end up with a single element in either the left or right array, so we use the JS spread operator to merge left and/or right with the result array.

![](https://i.imgur.com/5K4zKb3.png)

And finally, here is the full implementation:

![](https://i.imgur.com/ozwhF57.png)

Sources:   

[Four Semesters of Computer Science in Five Hours ](https://www.lynda.com/JavaScript-tutorials/Four-Semesters-Computer-Science-5-Hours/604270-2.html)

[Wikipedia](https://en.wikipedia.org/wiki/Merge_sort)

[Khan Academy](https://www.khanacademy.org/computing/computer-science/algorithms/merge-sort/a/overview-of-merge-sort)


