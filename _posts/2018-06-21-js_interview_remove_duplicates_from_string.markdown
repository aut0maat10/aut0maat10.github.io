---
layout: post
title:      "JS Interview: Remove Duplicates from String"
date:       2018-06-21 22:52:03 +0000
permalink:  js_interview_remove_duplicates_from_string
---

![Many Benders](https://i.imgur.com/BtBCliA.jpg)

In a recent interview situation, I was asked to write a JavaScript function to remove all duplicates from a string, so that an example input of ‘aabadabcd’ would return ‘abdc’. I chose to use a [JavaScript Set](https://alligator.io/js/sets-introduction/) to tackle the problem, but struggled a bit when asked to come up with an alternative solution. This started bothering me a bit, so I decided to explore some other solutions to the problem.

But first, here’s my initial implementation, using a JS Set:

```
const removeDuplicates = (input) => {
   const mySet = new Set(input);
   const unique = Array.from(mySet);
   return unique.join('');
}
removeDuplicates(‘aabadabcd’); //=> "abdc"
```

The JS Set object was introduced in ES6. What makes it useful in this context is that it only allows unique values, so when you pass in the input (e.g. a string or array with duplicates), the set will remove all the duplicates and store only unique values. 

My initial implementation was actually a bit verbose, so a cleaner, one-line version would look like this:

```
const removeDuplicates = (input) => {
   return Array.from(new Set(input)).join('')
}
removeDuplicates(‘aabadabcd’); //=> "abdc"
```

**Alternative Solutions**

I wanted to first find a brute-force solution as an alternative. After some research, I came up with a solution using a for loop and the JS `indexOf()` - method. 

**JS indexOf() Method**

```
const removeDuplicates = (input) => {
  let unique = [];
  let arr = input.split('');
  for (let i = 0; i < arr.length; i++) {
    if (unique.indexOf(arr[i]) === - 1) {
      unique.push(arr[i]);
    }
  }
  return unique.join('');
}
removeDuplicates(‘aabadabcd’); //=> "abdc"
```

Here, I split the string into an array, loop through it, and push unique values to a new array called `unique`. I use the `indexOf()` method to see if the current character already has been pushed into the `unique` array. The `indexOf()` method returns `-1` if the character is not found in the array you are inspecting. Therefore, if the comparison returns `-1`, we know that the current character does not yet exist in the `unique` array, so we push the character into the array and end up with only the unique characters.

**JS  Filter Method**

Let’s try one final example with the JS `filter` method. The `filter` method applies the callback function on each element in the array that you are inspecting. You can provide arguments to `filter` through an array and return the values that pass the filter — for instance, if you had an array of numbers, you could filter through the array to return all numbers smaller than 5:

```
const arr = [3, 1, 6, 8, 2, 9, 52];
const smallerThanFive = arr.filter(element => element < 5);
console.log(smallerThanFive); // => [3, 1, 2]
```

But the `filter `callback function can take in additional arguments, too. In this case, we are using three: 

* `element` = current element
* `index` = index of the current element
* `array` = the array object that contains the element

This is how we would use the` filter` method to remove duplicates from a string:  

```
const removeDuplicates = (input) => {
  return input.split("").filter((element, index, arr) => { 
    return arr.indexOf(element) === index }).join("");
}
removeDuplicates('aabadabcd'); // => "abdc"
```

Since the `indexOf() `method returns the *first occurrence* of a specified value in an array, we can compare it to the index of the current element. If the `index` of the current `element` does not match the result of the `indexOf()` method, the qualifications have not been met, and the `filter` method will skip the current `element` (since in this case, it’s a duplicate).

And with that, we now have three ways to remove duplicates from a string with a JavaScript function.


**Links**

[JS Set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set)

[JS indexOf() Method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)

[JS Filter Method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

