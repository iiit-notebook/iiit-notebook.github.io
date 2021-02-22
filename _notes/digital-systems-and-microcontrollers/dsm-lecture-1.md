---
title: DSM Lecture 1
code: ec2.101
author: Pratyaksh Gautam
date: 2020-02-19
number: 1
---
## Revising Number Systems
We use base 10 (decimal) number system in day to day life, it *feels* the most natural to us as a result, but we could have just as well used any other base as well.
When we're counting up ...
```
0 1 2 3 4 5 6 7 8 9 _10_
```
...something interesting happens after '9', we have a double-digit number, and the reason we do this is that in base 10, we have no symbol to directly represent a number greater than 9.  
So we (improvise, adapt, and) overcome this by writing it as 10, and this represents $1 \times 10^1 + 0 \times 10^0$.  
We've learned this without really paying much attention to the exponents in the past, as the order of *place values* from right to left (or from *least significant to most significant*), as ones, tens, hundreds, thousands etc.

*Note: "10 doesn't exist as a number in the system yet, so how did you represent it as $10^1$?"  
This we can simply hand-wave away, since we can still use any other symbol to represent the value right after 9; that value itself still exists, though we are still figuring out its representation.  
Here we simply use '10' as the representation for that number before the fact.*

This general pattern can be continued on for *any number* and in **any base**, there is nothing decimal specific about it.  
Consider writing the number $(5)_{10}$ in binary, we can write it as:  
$$(5)_{10} = 1 \times 2^2 + 0 \times 2^1 + 1 \times 2^0 = (101)_2$$

This system generalises further to represent fractional numbers, for example $\frac{1}{2}$ in decimal:  
$$\frac{1}{2} = 0 \times 10^0 + 5 \times 10^{-1} = (0.5)_10$$  
and in binary:  
$$\frac{1}{2} = 0 \times 2^0 + 1 \times 2^{-1} = (0.1)_2$$

In both of the above we use the 'radix point' to denote the split between the whole number part and the fractional part.
