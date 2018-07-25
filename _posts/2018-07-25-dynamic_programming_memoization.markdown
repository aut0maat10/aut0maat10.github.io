---
layout: post
title:      "Dynamic Programming: Memoization"
date:       2018-07-25 20:37:38 +0000
permalink:  dynamic_programming_memoization
---


![](https://i.imgur.com/xHcTNXy.jpg)

Recursive functions often waste time recalculating the same results over and over again. A perfect example of this is the [Fibonacci number](https://en.wikipedia.org/wiki/Fibonacci_number) generator:

```
const fibonacci = (n) => {
  if (n <= 2) {
    return 1;
  }
  else {
    return fibonacci(n - 1) + fibonacci(n - 2);
  }
}
```

This function performs well for small values of `n`, but as `n` increases, the performance quickly becomes worse. This is because for every recursion, the same values get calculated over and over again. To calculate the 50th fibonacci number, the number of recursive calls is over 40 billion! [This video](https://youtu.be/P8Xa2BitN3I) explains well why this particular function is so ineffective. 

![](https://i.imgur.com/44R2jua.png)

It would be better if we could calculate any given `fib(n)` once, and then store the value and look it up when needed. This is where memoization and dynamic programming comes in.

**Memoization**

Memoization is a programming technique that increases a function’s performance by caching previously calculated results. In JavaScript, objects are ideal for caching. Each time a memoized function is called, the parameters are used to index the cache. If the data exists in the cache, it can be returned without executing the entire function, which saves time.

```
const fibonacchi = (() => {

  const cache = {};

    function fibo(n) {

    let value; 

    if (n in cache) {
      value = cache[n];
    } else {
      if (n === 0 || n === 1) {
        value = n;
      } else {
        value = fibo(n -1) + fibo(n - 2);
        cache[n] = value
      }
    }
    return value;
  }
  return fibo;
})();

console.log(fibonacchi(50)) // => 12586269025
```

In this example, we use an anonymous [IIFE](https://en.wikipedia.org/wiki/Immediately-invoked_function_expression) that returns an inner function `fibo`, which serves as the fibonacci function. 

First, we declare an object to use as a cache. Next, we declare an inner function in which we use the in operator to check if the current value already exists in the cache object. If it exists, the cached value is returned. Otherwise, the original fibonacci code is executed. 

Compared to the original, recursive function, which needed more than 40 billion calls to compute the 50th fibonacci number, our new function that utilizes memoization only needs 99.

**Links: **

[Fibonacci Numbers (Wikipedia)](https://en.wikipedia.org/wiki/Fibonacci_number)

[HackerRank: Memoization (video)](https://youtu.be/P8Xa2BitN3I)

[Implementing Memoization in JavaScript](https://www.sitepoint.com/implementing-memoization-in-javascript/)







