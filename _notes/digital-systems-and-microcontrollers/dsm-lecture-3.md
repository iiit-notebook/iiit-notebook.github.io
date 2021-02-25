---
title: DSM Lecture 3
code: ec2.101
author: Pratyaksh Gautam
date: 2020-02-24
number: 3
---

## Representing negative binary
At the hardware level, we represent sign with a single **sign bit**, conventionally 0 for positive, and 1 for negative.

### Signed magnitude representation
In this notation, the number is represented with a sign bit along with the magnitude of the actual number.
The signed bit is but in the most significant bit position. For eg.
$$(1011)_2 = - (011)_2 = -3$$

However it has one limitation, we have both +0, and -0, when we only really need (and want to deal with) one value of zero.

### Signed complement representation
It is more convenient at the hardware level, to instead represent negative numbers by its complement.  
Positive numbers are represented directly in this notation, and negative numbers are represented by taking the magnitude of the number, then complementing it. For eg. for the number -7 in a 4 bit, signed 2's complement representation:

$(-7)$, for it's magnitude (7), we have $(7)_{10} = (0111)_2.$  
Then, we take its two's complement, getting $(1001)_2$

<!-- Add table for representations of numbers in 4-bits -->

### Signed addition
If we have numbers in memory represented in 2's complement form, we just need to add the two numbers (including the sign bit),
and we get the correct answer, itself already in 2's complement form.

**Note***: We must take care that our result will be within the range of our n-bit representation, else overflow occurs.*

### Signed subtraction
Subtraction of two signed binary numbers in 2's complements form is simple:
*Note: (minuend - subtrahend)*

1. Take the 2's complement of the subtrahend, and add it to the minuend.

2. If carry is present, the result is positive. Drop the carry and you have your result.

3. If carry is not present, the result is negative. Take the 2's complement and you have your result.

## Binary Codes
Any discrete element of information that is distinct among a group of quantities can be represented with a binary code.

### Binary Coded Decimal (BCD)
This code is the most commonly used, and is simply the direct representation of decimal numbers to binary numbers.  
The numbers (0 - 9) can be represented using 4 binary digits, with some wastage, the values (10 -15) are undefined.

We represent each digit in the decimal representation of the number as a binary nibble (4-bit group).  
Any number with $k$ decimal digits will require 4$k$ bits in BCD.

*Note: In signed BCD 0 is positive sign, and 9 is negative sign.*

### Representing Characters
ASCII and Unicode

### Representing fractions

#### Fixed point representation
This is the easier way, where we assume the radix point to be present at some arbitrary, but fixed point.

#### Floating point representation
This is a more sophisticated method, where we have a mantissa and an exponent.  
The **mantissa** contains the significant bits of the number, and the **exponent** tells us where the radix point sits.

We convert the number to be stored as
$$N = M \times r^e$$
and then store $M$ and $e$ as binary.
