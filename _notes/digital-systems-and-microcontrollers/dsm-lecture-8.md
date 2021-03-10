---
title: DSM Lecture 8
date: 2021-03-08
author: Pratyaksh Gautam
code: ec2.101
number: 8
---

## Karnaugh maps
Karnaugh maps of **k-maps** are a useful visualization of truth tables.
They are very useful for minimizing our logical circuit into a simpler gate logic representation.

We define regions within the k-map, where we have a value for a given variable:

### 2 variable k-map
| x y | 0    | 1   |
| --- | ---  | --- |
| 0   | x'y' | x'y |
| 1   | xy'  | xy  |

The 0 and 1 in each row and  column tell us the value of the variable, and the cells thus represent each minterm.

## 3 variable k-map
| x yz | 00    | 01    | 11   | 10    |
| ---  | ---   | ---   | ---  | ---   |
| 0    | x'y'z | x'y'z | x'yz | x'yz' |
| 1    | xy'z' | xy'z  | xyz  | xyz'  |

The important property of the map useful to us is that *adjacent squares in the map differ only by one variable*,
which is primed in one square and unprimed in the other. This allows us to do some very helpful logic gate minimizations.  
