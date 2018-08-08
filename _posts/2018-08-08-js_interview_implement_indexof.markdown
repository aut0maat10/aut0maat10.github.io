---
layout: post
title:      "JS Interview: Implement indexOf()"
date:       2018-08-08 20:53:26 +0000
permalink:  js_interview_implement_indexof
---


In an interview situation a while back, I was asked to implement my own version of the JavaScript method ` indexOf()`.

```
const indexOf = (arr, n) => {

   // your code here
	 
}
```

The function takes in an array of numbers `arr` and an integer `n`. The task is to find the index of `n` in `arr`. According to the [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf): 

> The `indexOf()` method returns the first index at which a given element can be found in the array, or -1 if it is not present.
> 

This sounds pretty straight-forward. First, you loop through the array, and if `arr[i]` equals `n`, the index of `n` will be ` i`. If `n` is not included in the array, you return `-1` after the loop finishes.

Here is my implementation:

```
const indexOf = (arr, n) => {
  for (let i = 0; i < arr.length; i++ ) {
    if (arr[i] === n) {
      return i;
    }
  }
  return - 1;
}

indexOf([2, 5, 7, 8], 5)) // => 1
indexOf([2, 5, 7, 8], 8)) // => 3
indexOf([2, 5, 7, 8], 3)) // => -1
```

You could make the function slightly faster by storing the length of the array in a variable, and thus avoid calculating the length for every iteration. The final implementation looks like this:

```
const indexOf = (arr, n) => {
  const len = arr.length;
  for (let i = 0; i < len; i++ ) {
    if (arr[i] === n) {
      return i;
    }
  }
	return -1;
}
```

**Links:**

[MDN Docs: Array.prototype.indexOf()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)








