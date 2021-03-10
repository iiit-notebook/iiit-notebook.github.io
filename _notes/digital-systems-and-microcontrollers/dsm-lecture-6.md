---
title: DSM Lecture 6 notes
date: 2021-03-03
code: ec2.101
author: Pratyaksh Gautam
number: 6
---
## Canonical Forms
Any boolean expression in n variables can be converted into the canonical form by algebraic manipulation.

<!-- Write about SOP and POS forms, how to obtain them algebraically, how to obtain them from truth tables -->

## Standard forms
A boolean expression can be represented in the standard form, which is also a POS or an SOP representation,
but here we do not have the requirement that each term must have all the variables in it.  
Essentially we are looking for a boolean expression that can represent the number with exactly two "layers" of gates.

## Boolean functions
We can have $2^{2^n}$ functions in n binary variables.

| $x$ | $y$ | $F_0$ | $F_1$ | $F_2$ | $F_3$ | $F_4$ | $F_5$ | $F_6$ | $F_7$ | $F_8$ | $F_9$ | $F_10$ | $F_11$ | $F_12$ | $F_13$ | $F_14$ | $F_15$ |<!--{{{-->
| --- | --- | ---   | ---   | ---   | ---   | ---   | ---   | ---   | ---   | ---   | ---   | ---    | ---    | ---    | ---    | ---    | ---    |
| 0   | 0   | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 1     | 1     | 1      | 1      | 1      | 1      | 1      | 1      |
| 0   | 1   | 0     | 0     | 0     | 0     | 1     | 1     | 1     | 1     | 0     | 0     | 0      | 0      | 1      | 1      | 1      | 1      |
| 1   | 0   | 0     | 0     | 1     | 1     | 0     | 0     | 1     | 1     | 0     | 0     | 1      | 1      | 0      | 0      | 1      | 1      |
| 1   | 1   | 0     | 1     | 0     | 1     | 0     | 1     | 0     | 1     | 0     | 1     | 0      | 1      | 0      | 1      | 0      | 1      |<!--}}}-->

:All the 16 functions possible for the boolean variables $x, y$
