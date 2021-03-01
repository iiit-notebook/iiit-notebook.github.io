---
title: DSM Lecture 5
date: 2020-03-01
author: Pratyaksh Gautam
code: ec2.101
number: 5
---
## Logic Gates
We represent binary signals in digital systems as high voltage (1), and low voltage (0) signals.
For example, Arduino reads 3-5V as HIGH, or *true* and 0.-1.5V as LOW or *false*.  
*Note: Other than NOT gate, logic gates can have more than two inputs*

![img-50](/assets/images/dsm_lec5_img1.png)

### Boolean Functions
A **boolean function** described by a boolean expression has binary variables, and constants 0, and 1, and logic operation symbols.
The function must return a value of either 0, or 1. eg. $F = x + y.z$

Boolean functions can be represented as a truth table, and the number of rows is given by $2^n$, where n is the number of variables in the function. For each boolean function we have one, and only one, truth table.
Multiple algebraic forms may have the same truth table; in that case they are equivalent statements or functions.

By manipulating a boolean expression according to the rules of boolean algebra, it is sometimes possible to obtain simpler expressions, reducing the complexity of the circuit representing it.

### Complement of a function
The complement of a function F is the function such that it outputs 0 when F outputs 1, and vice versa.
We can also derive the complement algebraically:
<div>
$$
\begin{align}
			F  &= x + y'z \
\Rightarrow	F' &= x'.(y'z)' \
			   &= x'.(y + z') \
\end{align}
$$
</div>

The generalized form of DeMorgan's theorem states that you can 

### Minterms
A **minterm** is a *standard product*, for $n$ binary variables, we can have $2^n$ possible minterms.  
For eg. with variables x and y

<div>
| x | y | $m_i$		 |
|---|---| --- 		 |
| 0 | 0 | $m_0: x'y'$|
| 0 | 1 | $m_1: x'y$ |
| 1 | 0 | $m_2: x'y$ |
| 1 | 1 | $m_3: xy$  |
</div>

### Maxterms
Similarly we have **maxterms**, which are *standard sums*.  
For eg. with variables x and y

<div>
| x | y | $M_i$		     |
|---|---| --- 		     |
| 0 | 0 | $M_0: x + y$   |
| 0 | 1 | $M_1: x + y'$  |
| 1 | 0 | $M_2: x' + y$  |
| 1 | 1 | $M_3: x' + y'$ |
</div>
