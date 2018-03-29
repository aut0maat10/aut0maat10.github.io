---
layout: post
title:      "Binary Search"
date:       2018-03-29 01:16:59 +0000
permalink:  binary_search
---


*I recently graduated from Flatiron School’s Full Stack Web Development Online Program. After six months of programming in Ruby and Javascript, I have seen my main interest gradually shift from frontend to backend design. Consequently, as I am now entering the job search program, part of my daily routine is to focus on computer science, data structures, and algorithms. The purpose of this blog is to document and articulate the things I learn.*

### Let's Talk about Binary Search!

The main concept in binary search is to repeatedly divide into half a sorted list of items which could contain the item, until you have narrowed down the possible locations to only one. Binary search is an effective algorithm for finding an item from an *ordered list* of items. 

### How Efficient is Binary Search?

Say you want to find a name in a phone book (for instance last name “Smith”). With linear search, you would have to start at “A” and work all the way through the alphabet until you reach “S”. Most people would probably open the phone book roughly at the middle, and work their way forward (or back) in order to find the “S” section. Binary search uses a similar method. When binary search makes an incorrect guess, the portion of the array that contains reasonable guesses is reduced by at least half. 

If you have an array of 8 elements, an incorrect guess reduces the size of the reasonable portion to 4, than 2, then 1. When one item remains, the final guess is either correct or incorrect, and we’re done. With an array of 8 elements, we need at most 4 guesses. The neat thing is that even if you double the array, we will need at most one more guess. 

The worst case of guesses for an array of *n* elements is the number of times we can divide it in half (starting at *n*), until we get the value 1. As a mathematical function, this is expressed as** base-2 logarithm of *n***.

#### Table of base-2 logarithms of various values of *n*:

![](https://i.imgur.com/N4P7EEJ.pnghttp://)

So, even with an array of 1,048,576 items, with binary search, we would need no more than 21 guesses (20 + 1) to find our item! Compare that to worst case of linear search = 1,048,576 guesses. Consequently, the Big O for binary search is **O(log n)**

### Pseudocode for Binary Search:

* Let `min` = 0 and `max` = n -1
* If `max < min`, then stop. `target` is not in array.
* Let `guess` be the average of `max` and `min`, rounded down to an integer
* If `array[guess]` is equal to `target`, you found it! Stop and return `guess`.
* If the `guess` was too low, that is, `array[guess] < target`, then set `min = guess + 1`.
* Else, the `guess` was too high. Let `max = guess -1`.
* Return to step 2.

### JavaScript Code: 

```
const binarySearch = (arr, target) => {
  let min = 0
  let max = arr.length - 1
  let guess; 
  while (min <= max) {
    guess = Math.floor((max + min) / 2);
    if (target === arr[guess]) {
      return guess
    } else if (arr[guess] < target) {
        min = guess + 1
    } else {
        max = guess - 1
    }
  }
  return -1
}

console.log(binarySearch([1, 2, 3, 4, 5], 4)) // => 3 (index of 4)
```


#### For a more detailed description of binary search, see [this section on Khan Academy](https://www.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search)
