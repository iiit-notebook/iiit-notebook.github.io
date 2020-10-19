---
title: C Pro Lecture 16
author: Pratyaksh Gautam
code: cs0.101
number: 16
---

## Complexity and 'work done'

Processors work at a near constant rate of elementary instructions executed per second. So the time taken by a program to execute is effectively proportional
to the *number of elementary instructions needed to execute the program*.  
Suppose that a program can be subdivided into 3 parts, having $k_{1}$, $k_{2}$ and $k_{3}$ instructions respectively. 
Now further, let's say that the second subpart of the problem runs as a loop, it runs on input of size `N`, then this entails that the total time taken by the program to execute should be proportional to $k_{1} + N \times k_{2} + k_{3}$.

When we discuss the "time complexity" of the program, we are talking not about the exact runtime of the program (which is dependent also on the processor speeds),
but **how the program execution time scales with its input data**. We make what is known as a *constant factor approximation*, and ignore all the constant terms, terms independent of `N` and only care about the *fastest growing* part of the program.
This is what best tells us how the program scales with its input data.

Suppose the *time complexity* of a program is best defined by 
$$ T(n) = k_{1} N^2 + k_{2} N + k_{3} $$
Then we can take the constant factor approximation by simply caring about only the most dominant term in the equation as the data scales, the quadratic term in this case.
We can also remove the constant attached to it for our purposes, giving us the time complexity of $N^2$.

