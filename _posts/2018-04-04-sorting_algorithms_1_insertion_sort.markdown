---
layout: post
title:      "Sorting Algorithms 1: Insertion Sort"
date:       2018-04-04 22:29:53 +0000
permalink:  sorting_algorithms_1_insertion_sort
---


*I recently graduated from Flatiron School’s Full Stack Web Development Online Program. After six months of programming in Ruby and Javascript, I have seen my main interest gradually shift from frontend to backend design. Consequently, as I am now entering the job search program, part of my daily routine is to focus on computer science, data structures, and algorithms. The purpose of this blog is to document and articulate the things I learn.*

## Sorting a list of items (e.g. an array of numbers or strings) into ascending or descending order can help a computer or a human quickly find items in the list. Understanding sorting is a traditional first step of understanding algorithms and computer science. 

(I chose to omit bubble sort from this list of sorting algorithms, since it's terribly inefficient and therefore pretty much never useful. If you want to learn more about bubble sort, you can do so here.) 

## Insertion Sort

Unlike bubble sort, insertion sort is an occasionally useful sorting algorithm. It works well for arrays that are very close to sorted. However, its worst case scenario (i.e. when implemented on a randomly sorted array) is close to bubble sort's. 

![Insertion Sort: A Visualization](https://www.codeproject.com/KB/recipes/SortVisualization/Insertion_Sort.gif)


With insertion sort, we divide the initial, unsorted array into two parts: sorted and unsorted. Initially, there is only one element in the sorted part. We then go through the unsorted part one element at a time, inserting it in the correct position in the sorted. 

## Below is one way to implement insertion sort on an array of numbers, using nested for loops. 

![](https://i.imgur.com/gj5XBsL.png)

The outer loop signifies where the sorted part is: We start the outer loop at index 1, because we consider the first element in the array (index 0) to already be sorted. When i moves to 2, everything before 2 is sorted, which also means that everything after index 2 is unsorted. 

The inner loop is going over only the sorted part of the array (`j < i`). If the number at index `i` (which is the first unsorted element) is smaller than than the number at index` j`, we are going to remove it from its current position and store it in a variable `spliced` using the Array splice method. Then, using splice again, we are going to insert it at the index of `j` .

Finally, we are going to return the sorted array. 

The time complexity of insertion sort is O(n²), but as mentioned before, it's still useful for arrays that are close to sorted. Compare time complexity of sorting algorithms at http://bigocheatsheet.com/ .

It took me a while to wrap my head around how exactly the nested for loops work together, but once you understand the concept, the code makes perfect sense. For this implementation, it is also crucial to understand how the Array splice() method works. [Read more about that one here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice). 








