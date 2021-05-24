---
title: CSO Lecture 1
date: 2021-05-19
author: Pratyaksh Gautam
code: cs2.201
number: 1
---

## Von Neumann Architecture

The von Neumann architecture refers to the computer architecture having a separate memory and central processing unit,
where both the program instructions and data are both stored in the separate memory.

![img-50](/assets/images/Von_Neumann_Architecture.jpg)

## Levels of Abstraction

When dealing with computers, we can work at varying levels of abstraction.
Working at a low level means being relatively close to the hardware in terms of design and operations,
and as a result often far from how humans think about the same larger operations.
Working at a high level means being closer to how humans think and organise the design and function,
but as a result it is often far from how the machine operations actually implement things.

## Instruction Set Architecture
Instruction set architecture (ISA) is a standardized set of instructions, data types, the features, and abstract structure,
and a given computer which has an *implementation* of the ISA is consistent with this structure,
and can handle the specified data types and instructions.

The implementations of the same ISA can vary for different models, however the consistency of the ISA allows programmers
to ignore the implementation details; they can work at a level of abstraction of the ISA itself.
This allows for greater portability and thus the ISA acts as a standardization.
