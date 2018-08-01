---
layout: post
title:      "Reverse a String In-Place"
date:       2018-08-01 20:59:52 +0000
permalink:  reverse_a_string_in-place
---

![](https://i.imgur.com/jKJuGzs.jpg)

When manipulating data, if often might be a good idea to work on a copy of the input in order not to create any unwanted side effects. However, occasionally an in-place algorithm might be a good way to save space. 

An in-place algorithm operates directly on its input and changes it. An in-place algorithm will generally have `O(1) `space cost.

Be careful, though: an in-place algorithm destroys the original input, so make sure you don't need the original input anywhere in your program!

Here is how you would reverse an array of characters nondestructively:

```
const reverse = (input) => {
  let result = [];
  for (let i = input.length - 1; i >= 0; i-- ) {
    result.push(input[i]);
  }
  return result;
}

reverseString(['a', 'b', 'c']) // => ['c', 'b', 'a']
```

And here is how you would do the same thing in place (by swapping elements):

```
const reverseInPlace = (input) => {
  let leftIndex = 0;
  let rightIndex = input.length - 1;

  while (leftIndex < rightIndex) {
    let temp = input[leftIndex];
    input[leftIndex] = input[rightIndex];
    input[rightIndex] = temp;

    leftIndex++;
    rightIndex--;
  }
  return input;
}

reverseInPlace(['a', 'b', 'c']) // => ['c', 'b', 'a']
```

The complexity of the in-place operation is `O(n)` time and `O(1)` space.
