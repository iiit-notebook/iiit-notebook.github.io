---
title: DSM Lecture 10
date: 2020-03-12
author: Pratyaksh Gautam
code: ec2.101
number: 10
---
## The Other states
Apart from the two states of 0 and 1, there is also the high impedance state denoted by Z.
If we dont connect a pin to either HIGH or LOW, the pin is said to be in a floating state or a Z state.

A **'Z'** state is akin to being disconnected, it does not affect the rest of the circuit anymore,
and this is of great importance in bus architectures, where we have multiple inputs that we want to constantly
'connect' and 'disconnect' from the bus.

We also have **"don't-care"** or X, which is not a state per-se, but is used to represent boolean values that we do not truly care about.
This is useful since we can choose them to be either 0 or 1 as and when convenient to us as designers.

A **multiplexer** is basically a data selector, given a n inputs and log(n) selectors,
it directs the selected input through to output.

A **demultiplexer** is similar, it takes one input, and directs it to a selected output.

