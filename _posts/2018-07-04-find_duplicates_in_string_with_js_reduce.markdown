---
layout: post
title:      "Find Duplicates in String with JS reduce() "
date:       2018-07-04 22:47:11 +0000
permalink:  find_duplicates_in_string_with_js_reduce
---

![](https://i.imgur.com/VOGfh9f.jpg)

Las week, I wrote about [removing duplicates from a string](http://electricsauna.net/js_interview_remove_duplicates_from_string) with JS methods` filter()` and `indexOf()`. But what if you wanted to return duplicate characters instead of removing them? After some more research, I learned a little trick with another JS method, i.e. `reduce() `.

According to the MDN docs, the `reduce()` method "applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value".

That means you can do this to sum all numbers in an array:

```
const numbers = [1, 2, 3, 4];
const reduced = numbers.reduce((accumulator, currentValue) => accumulator + currentValue)
console.log(reduced) // => 10
```

The `reduce()` method also takes additional arguments, including an initial value. If you wanted to add an initial value of 5 to the previous example, you could do this:

```
const numbers = [1, 2, 3, 4];
const reduced = numbers.reduce((accumulator, currentValue) => accumulator + currentValue, 5)
console.log(reduced) // => 15
```

`reduce()` also takes arguments for the index of the current element, as well as the array you are applying the method to. The full list of arguments looks like this:

`array.reduce(function(accumulator, currentValue, currentIndex, arr), initialValue)`

In our case, we want to find and return duplicates in a string. First, we split our input string into an array, and call `reduce()` on that array. The trick here is setting the `initialValue` of `reduce()` to an array (line 7 in the example below), and then we can push duplicates to that array. 

The callback also takes parameters for `currentElement`, `currentIndex`, and ` arr` (which in this case refers to the input string split into an array of characters). Next, we use `indexOf()` to compare for duplicates, and if we get an indication of duplicates, we push the character to the `duplicatesArr`. 

To avoid duplicates in the duplicatesArray, we also check for the current element there (`indexOf()` returns `-1` if current element is not found). The final code looks like this:

```
const returnDuplicates = (input) => {
  const duplicates = input.split('').reduce((duplicatesArr, currentElement, currentIndex, arr) => {
    if (arr.indexOf(currentElement) !== currentIndex && duplicatesArr.indexOf(currentElement) === -1) {
      duplicatesArr.push(currentElement); 
    }  
    return duplicatesArr;
}, []);
  return duplicates.join('');
}

returnDuplicates('aaabbbcccdeffffff'); // => abcf
```

**Links:**

[MDN docs: Array.prototype.reduce()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

[MDN docs: Array.prototype.indexOf()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)

