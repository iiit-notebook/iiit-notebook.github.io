---
title: CSO Lecture 5 notes
author: Pratyaksh Gautam
date: 2021-06-02
code: cs2.201
number: 5
---

## Instruction Set Architecture

There may be hardware optimizations below the layer of abstraction of the ISA, but it is assumed
that even after these optimizations the processor still executes instructions sequentially.

The processor may execute many instructions concurrently, but safeguards are employed to ensure
that the behaviour matches that of sequential execution.

## x86 Architecture and Semantics

**Fetch-decode-execute** cycle is the most fundamental idea for the machine semantics of the x86.

In the instruction format, commonly used instructions and instructions with fewer operands
require a smaller number of bytes to represent. They can range in length from 1 to 15 bytes in IA32.
