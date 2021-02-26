---
title: DSM Lecture 4
date: 2020-02-26
author: Pratyaksh Gautam
code: ec2.101
number: 4
---
## Binary Logic
Binary logic deals with variables that take on two discrete values, which we often represent with 1s and 0s, *true* and *false* etc.

### Basic operations of Boolean algebra

1. **NOT**: represented by a prime or an overbar, it is a unary operator which turns a 1 to a 0, and vice versa

2. **AND**: represented by a dot or the absence of an operator, it is a binary operator which results in a 1 only when both of its operands are 1, else it results in a 0.

3. **OR**: represented by a plus sign, it is a binary operator which results in a 0 only when both of its operands are 0, else it results in a 1.

Below we have the *truth tables* for these basic operations:
![img-75](/assets/images/truth_tables_basic.png)

### Formalization of Boolean algebra
A *binary operator* defined on a set $S$ of elements is a rule that assigns, to each pair of elements from S, a single element from S.

The basic operations NOT, AND, OR are closed, and AND and OR are associative, and commutative in nature.
The operator AND is distributive over OR, i.e. $x.(y + z) = (x.y) + (x.z)$, and the operator OR is distributive over AND, i.e. $x + y.z = (x + y).(x + z)$

In boolean algebra, proofs by truth table are valid, essentially being an exhaustive case analysis. 

The *duality principle* and states that every algebraic expression deducible from the postulates of boolean algebra remains valid
