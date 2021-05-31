---
title: CSO Lecture 4 Notes
author: Pratyaksh Gautam
date: 2021-05-31
code: cs2.201
number: 4
---

### Automatic conversion risks

Upon typecasting a negative signed integer to an unsigned integer, we can end up with
a large positive integer instead. This is why if we are not careful about type conversions,
we may introduce bugs.

```
11111111 {signed} -> 11111111  {unsigned}
```

## Integer overflow
Integer addition can also bring about overflow errors, when the sum of the integers
exceeds the limit of the data type.

For eg.
```
 1010
+0111
-----
10001
-----
```
Here, assuming 4 bit integers, only the least significant 4 bits survive,
leaving us $(0001)_2$ instead of the actual answer.

This is a case of overflow, we can have underflow as well, when we subtract integers and the result
is below the representable range.

For other operations such as negation and multiplication also, we are effectively working
in the field of integers modulo $2^{w}$, where *w* is the size of the data type in bits.

[See the last few slides of this for signed binary number multiplication](https://faculty-web.msoe.edu/johnsontimoj/Common/FILES/binary_multiplication.pdf)

## Multiplication by constant

When multiplying by a constant, the compiler tries to speed up runtime, by
converting the constant to some power of 2 (or the closesest approximation).
Multiplication by a power of two can be executed very quickly by simply bit
shifting the number by the corresponding power of two to the left.
