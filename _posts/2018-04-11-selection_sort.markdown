---
layout: post
title:      "Sorting Algorithms 2: Selection Sort"
date:       2018-04-11 13:47:18 -0400
permalink:  selection_sort
---


*I recently graduated from Flatiron School’s Full Stack Web Development Online Program. After six months of programming in Ruby and Javascript, I have seen my main interest gradually shift from frontend to backend design. Consequently, as I am now entering the job search program, part of my daily routine is to focus on computer science, data structures, and algorithms. The purpose of this blog is to document and articulate the things I learn.*

**Selection sort is another simple sorting algorithm. Like bubble sort, its running time is O(n^2), even though selection sort is slightly more efficient when *n* is large. Like bubble sort, selection sort is a good introduction to sorting algorithms, but you would probably not implement them in a real-world application.**

Selection sort loops over positions (indices) in the array, comparing the current element in the list to every other item in the subarray starting at the current position. In other words, it finds the index of the minimum value in the subarray, and swaps positions between the minimum value and the value at the current position.

![Selection sort visualization](http://codepumpkin.com/wp-content/uploads/2017/10/SelectionSort_Avg_case.gif)

## Pseudocode
**Example: sort an array of numbers using selection sort**

1. Find the smallest number. Swap it with the first number.
2. Find the second-smallest number. Swap it with the second number.
3. Find the third-smallest number. Swap it with the third number.
4. Repeat until the array is sorted.

## Swap

A common step in many sorting algorithms is to swap two elements in an array. Here's an example of a simple swapping function:

![](https://i.imgur.com/gObVnC0.png)

## Find Index of Smallest Number

Another key element of selection sort is to find the index of the smallest number in the subarray. We can do that with another helper function:

![](https://i.imgur.com/3MUiTa8.png)

This is useful for the selection sort algorithm, because you look for the index of the smallest number with every new iteration. That means you adjust the `startIndex` for every index in the array.

This is how you would implement selection sort using the helper functions explained above:

![](https://i.imgur.com/DmUKDsn.png)

... and here is the full code:

![](https://i.imgur.com/Yty9BrL.png)



## Sources: 

[Big-O Cheat Sheet](http://bigocheatsheet.com/)

[Khan Academy (Sorting)](https://www.khanacademy.org/computing/computer-science/algorithms/sorting-algorithms/a/sorting)

[Selection Sort (Wikipedia)](https://en.wikipedia.org/wiki/Selection_sort)






