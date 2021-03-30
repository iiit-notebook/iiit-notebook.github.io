---
title: Linear Algebra Lecture 16
date: 2021-03-23
author: Pratyaksh Gautam
code: ma2.101
number: 16
---

Consider the set of of all functions of the form $F = \{ f: \{0, 1\}^n \rightarrow \mathbb{R} \}$
Let us consider this over the field of real numbers. We define vector addition and multiplication as such:
$$h = f + g \implies h(x) = f(x) + g(x)$$
$$h = \alpha g \implies h(x) = \alpha \cdot g(x)$$
Then this forms a vector space.

Consider the dimension of the simple case where $n = 1$, then $F = \{ f: \{0, 1\}^n \rightarrow \mathbb{R} \}$.  
In order to find the dimension, we must find a basis for the space.
Let the basis be defined by two functions $f_1, f_2$, such that
$$f_1(0) = 0,\ f_1(1) = 1$$
$$f_2(0) = 1,\ f_2(1) = 0$$

Then given $a, b \in \mathbb{R}$, we can represent any function in $F$ as
$$ a \cdot f_1 + b \cdot f_2 $$
Thus, the dimension of the vector space must be 2 in this case.

Similarly, for greater values of n, we can consider the possible values of $f_i$ at $x = 0$ and $x = 1$, which can be either $0$ or $1$ again, and use this as one of the basis vectors.  
We can reason that thus, there must be $2^n$ such basis vectors and as a result, we can say that the dimension of the vector space $F$ is $2^n$.

<!-- TODO (row rank = column rank) proof -->

<!-- TODO graph adjecency probability calculation for random walk -->
