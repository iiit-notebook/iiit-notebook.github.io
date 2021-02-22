---
title: DSM Lecture 2
code: ec2.101
author: Pratyaksh Gautam
date: 2020-02-22
number: 2
---

## Complements of numbers
Complement operations are run on a single number in any given base, and can simplify succeeding operations in digital circuits.

### Diminished radix complement
Given a number $N$ in base $r$ having $n$ digits, the $(r-1)$'s complement of $N$, i.e., its diminished radix complement is defined as $(r^n - 1) - N$

*Note: n is the number of digits that we choose for all of our representations (most often the word size in our hardware representation)*

### Radix complement
The $r$'s complement of an n-digit number $N$ in base $r$ is defined as $r^n - N$ for $N \neq 0$ and as 0 for $N = 0$.

Comparing with the diminished radix complement, we can achieve one from the other by subtracting 1.

### Some notes on Complements
If the original number N contains a radix point, the point should be removed temporarily in order to form the r's or (r - 1)'s complement.  
The radix point is then restored to the complemented number in the same relative position.

In other words, we pretend the radix point doesn't exist while complementing numbers with radix points.

### Subtraction with Radix complements
Complementation makes it easier for use to perform subtractions in digital hardware.

Let's suppose we have to perform $M - N$ in base $r$:
1. Take the radix complement of N: $r^n - N$

2. Add this to M: $(r^n - N) + M = r^n + (M - N) = r^n - (N - M)$ 

3. If you get a carry in the $(n + 1)$th digit, then the result is positive, discard the carry and you have the result.  
	Since $r^n$ will be represented as 1, followed by n 0s, so removing the carry is equivalent to ignoring the $r^n$, and we are left with only $(M - N)$

4. If you do not get a carry in the $(n + 1)$th digit, then the result is negative. Take the radix complement of the number to get the answer, then put a negative sign.  
	Since $r^n - (N - M)$ is the complement of $(N - M)$, so taking the radix complement of this again, we get $(N - M)$ back. Then putting a negative sign in front of it, we get $(M - N)$, the result we wanted.

Though it may seem a bit convoluted, this method removes the need for borrowing, which requires us to know the value of the next digit in the number.

## Subtraction with diminished radix complements
Similarly for diminished radix complements.

1. Take the diminished radix complement of N: $r^n - 1 - N$

2. Add this to M: $r^n - 1 - N + M = r^n + (M + N - 1) = (r^n - 1) - (N - M)$

3. If you get a carry in the $(n + 1)$th digit, then the result is positive, add the carry to the result and you are done.

4. If you do not get a carry in the $(n + 1)$th digit, then the result is negative, take the diminished radix complement of the number to get the answer then put a negative sign.

*Additional resource: [Radix and Reduced Radix subtraction](https://gato-docs.its.txstate.edu/slac/Subject/Math/Discrete/Radix-and-Reduced-Subtraction/Radix%20and%20Reduced%20Subtraction.pdf)*
