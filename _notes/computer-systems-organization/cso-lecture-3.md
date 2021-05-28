---
title: CSO Lecture 3 Notes
author: Pratyaksh Gautam
date: 2021-05-28
code: cs2.201
number: 3
---

## Storage Format

- Big Endian:
  The data inside a word is stored in left to right format,
  or most significant byte is stored leftmost.
  ```
  | 01 | 23 | 45 | 67 |
  ```
- Little Endian:
The data inside a word is stored in right to left format,
or least significant byte is stored leftmost.
  ```
  | 67 | 45 | 23 | 01 |
  ```

### Bitwise operations in C

### Integer ranges

#### Unsigned Integers

We take the decimal representation of a $w$ length bit string as
$\sum_{i = 0}^{w - 1} x_i 2^i$

#### Signed Integers

We take the decimal representation of a $w$ length bit string as
$(-1)^{x_{w - 1}} \sum_{i = 0}^{w - 2} x_i 2^i$

However, this would mean we have two zeros, eg. in 4 bits,
$(1000)_2$ and $(0000)_2$

In order to solve this problem, we use two's compliment representation

#### Signed Integers - Two's Complement Representation

$-(x_{w-1} 2^{w-1}) + \sum_{i = 0}^{w - 2} x_i 2^i$

## Isomorphism between binary, unsigned and two's complement integer arithmetic (modular)
The same bitstring can have a different numerical value depending on which system
it is interpreted in, unsigned or two's complement.

## Copying to an extended size datatype

If we want to copy a 4 bit unsigned integer to an 8 bit type,
we can just pad the 8 bit with 4 zero bits, and then the original 4 bit number.

For two's complement, if we have a positive number we do the same,
but if we have a negative number, we have to pad the 8 bit with 4 one bits,
and then the original 4 bit number.

For eg:
```
0011 -> 00000011 : signed or unsigned
1011 -> 11111011 : signed
```
