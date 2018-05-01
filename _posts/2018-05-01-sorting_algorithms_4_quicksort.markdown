---
layout: post
title:      "Sorting Algorithms 4: Quicksort"
date:       2018-05-01 16:52:39 -0400
permalink:  sorting_algorithms_4_quicksort
---


*I recently graduated from Flatiron School’s Full Stack Web Development Online Program. After six months of programming in Ruby and Javascript, I have seen my main interest gradually shift from frontend to backend design. Consequently, as I am now entering the job search program, part of my daily routine is to focus on computer science, data structures, and algorithms. The purpose of this blog is to document and articulate the things I learn.*

![](http://thetechnicgear.com/wp-content/uploads/2014/02/sorting-lego.jpg)

**Quicksort** is one of the most powerful sorting algorithms out there. Like [merge sort](http://electricsauna.net/sorting_algorithms_3_merge_sort), quicksort is a [divide and conquer ](https://www.khanacademy.org/computing/computer-science/algorithms/merge-sort/a/divide-and-conquer-algorithms) algorithm, which means it is *recursive*. You will need to have a solid understanding of [recursion](https://en.wikipedia.org/wiki/Recursion_(computer_science)) in order to effectively implement quicksort.

Quicksort and merge sort use divide and conquer in slightly different ways. In merge sort, the divide step hardly does anyting, and the real power lies within the merge phase. Quicksort is pretty much the opposite, since the divide step is where the magic happens, while the merge phase does nothing.

Quicksort's worst-case running time is as bad as [insertion sort](http://electricsauna.net/sorting_algorithms_1_insertion_sort)'s and [selection sort](http://electricsauna.net/selection_sort)'s, i.e. **O(n^2)**. Still, its average-case running time is the same as mergesort's, i.e. **O(n log n)**. In practice, however, quicksort outperforms merge sort. It also significantly outperforms insertion sort and selection sort. 

**Pseudocode for Quicksort**

1. Pick a **pivot**. In this case, we will use the last element in a list of numbers.
2. Construct two arrays, let's call them **left** and **right**. All elements smaller than the pivot go into the left array. All numbers greater than the pivot go into the right array.
3. Call quicksort on the left array and the right array independently.

Quicksort can be a bit hard to visualize at first, but [here's a good video walkthrough](https://www.youtube.com/watch?v=COk73cpQbFQ&t=111s) from **mycodeschool**. 


![Quicksort Visualization](https://img.wonderhowto.com/img/46/71/63594498633292/0/sorting-part-6-0-quick-sort-sorta-efficient.w654.jpg)
([Image source](https://0x00sec.org/t/sorting-part-6-0-quick-sort-sorta-efficient/202))

After left and right are sorted, we concatenate left, pivot, and right (in that order).

**JavaScript Implementation**

We start by declaring a function `quickSort` that takes an array (of numbers in this case) as an argument. Then, we establish the base case, i.e. an array with zero or one elements (an array with a single element is effectively sorted)

![](https://i.imgur.com/qJYaEM7.png)

Next, we pick the last element in the array and call it the `pivot`. We also declare the `left` and `right` arrays.

![](https://i.imgur.com/KU9xDEN.png)

Then, we loop through the original array and push elements smaller than the `pivot` to the `left` array. Elements greater than the `pivot` go into the `right` array. Note that we stop at the second to last element ( nums.length -1), since the `pivot`, which is the last element, should not be included.

![](https://i.imgur.com/X8KLMnN.png)

Finally, we recursively call `quickSort` on the `left` and `right` arrays. When the left hand side and the right hand side are independently sorted, we use the [JS spread operator](https://docs.microsoft.com/en-us/scripting/javascript/reference/spread-operator-decrement-dot-dot-dot-javascript) to concatenate `sortedLeft` with the `pivot` and  `sortedRight`.

![](https://i.imgur.com/jFy8YJN.png)

The full implementation of quicksort looks like this:

![](https://i.imgur.com/EkmKim9.png)

We can still make the code a little bit cleaner by placing the recursive call of  `quickSort` on  `left` and `right` directly in the concatenation stage:

![](https://i.imgur.com/tpc4ke6.png)

**Helpful Links**

[Overview of Quicksort](https://www.khanacademy.org/computing/computer-science/algorithms/quick-sort/a/overview-of-quicksort) (Khan Academy)

[Quicksort Walkthrough](https://www.youtube.com/watch?v=aQiWF4E8flQ&t=) (Harvard CS50)

[JavaScript Recursion](https://docs.microsoft.com/en-us/scripting/javascript/advanced/recursion-javascript) (Microsoft)

[Divide and Conquer Algorithms](https://www.khanacademy.org/computing/computer-science/algorithms/merge-sort/a/divide-and-conquer-algorithms) (Khan Academy)






