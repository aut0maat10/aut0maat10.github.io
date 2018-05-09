---
layout: post
title:      "CS and JS: Recursion"
date:       2018-05-09 17:44:42 +0000
permalink:  cs_and_js_recursion
---


After graduating from the Flatiron School, I have now entered the job search process. As part of my daily routine,  I have made an effort to keep learning on a daily basis. In addition to my continued studies of full stack JavaScript, I have devoted a part of my time to familiarize myself with CS concepts in general. This blog post is about **recursion**.

**General Definition: A Function That Calls Itself**

> Recursion in computer science is a method where the solution to a problem depends on solutions to smaller instances of the same problem (as opposed to iteration).
> 

You could also say that recursion is [the process of defining a problem (or the solution to a problem) in terms of (a simpler version of) itself](https://www.cs.utah.edu/~germain/PPS/Topics/recursion.html).

This means that ***a recursive function calls itself as part of its execution***. A good example is the factorial ***n*!**, which you might remember from math class. In mathemathics, the factorial function takes an integer ***n*** and multiplies all positive integers less than or equal to ***n***. Example: the factorial of 5 can be defined as  `5! = 5 * 4 * 3 * 2 * 1`.

In terms of programming, we will define the mathematical function ***n*!** as `factorial(n)`.

It might be helpful to split the solution into smaller pieces:

![](https://i.imgur.com/OJvb4l7.png)

This is effectively the same as:

![](https://i.imgur.com/lZ2zFLe.png)

Which in its turn can be defined as `fact(n) = n * fact(n - 1)`.

**Implementation: Base Case and Recursive Case**

In order to define a recursive function, you need to establish two things:

1. A **base case**, which will terminate the recursive progress.
2. A **recursive case**, which is where the recursion will occur.

In order to implement a recursive function in JavaScript, we first define the base case. When it comes to factorials, we want the recursion to stop when we reach the number 1:

![](https://i.imgur.com/LAVugIG.png)

Next, we define the recursive case:

![](https://i.imgur.com/0HMhaA8.png)

Finally, we can call the factorial function:

![](https://i.imgur.com/FqnFAQw.png)

**Links:**

[CS50](https://www.youtube.com/watch?v=mz6tAJMVmfM)

[Recursion (Khan Academy)](https://www.khanacademy.org/computing/computer-science/algorithms/recursive-algorithms/a/recursion)

[Recursion (Wikipedia)](https://en.wikipedia.org/wiki/Recursion_(computer_science))

















