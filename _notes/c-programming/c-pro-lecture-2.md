---
date: 2020-09-16
title: C Pro Lecture 2
author: Pratyaksh Gautam
code: cs0.101
number: 2
---
[The lecture recording](https://youtu.be/-4TbZzjYfsY)
## The CPU

The central processing unit itself is made up of a few components, namely - 
- **ALU** - stands for *arithmetic and logical unit*. It does the actual computations based on the instructions. 
- **PC** - stands for *program counter*. It retrieves the instructions from the appropriate memory address on the memory and increments itself according to the instruction length.
- **Bus** - it sends the instructions retrieved by the program counter from the memory to the CPU memory.
- **Registers/CPU Memory** - fast and efficient memory which is a part of the CPU itself. It contains multiple caches.

## The fetch-execute cycle

The CPU runs on a central clock, at a certain rate known as the **clock frequency**. This clock is used to synchronize the different components, and in one click tick, the CPU can fetch, decode and execute one instruction. A clock speed of 3.00 GHz means that the CPU clock ticks 3\*10^9 in a second. The fetch-execute cycle looks something like this - 
1. The program counter fetches an instruction from the appropriate address in memory.
2. The bus takes this to the instruction register in the CPU memory.
3. This instruction is then sent to the ALU where it is decoded and executed.

[Tom Scott's video on the topic](https://www.youtube.com/watch?v=Z5JC9Ve1sfI)

## The need for separate RAM and CPU registers

The RAM and CPU sit in physically separated units on the motherboard. The CPU registers are faster and more efficient than RAM, but at the same time are more expensive. As a result, in order to have the best performance at an economical price, we have small caches in the CPU that contain frequently accessed instructions and data, and comparatively larger RAM, from where all other needed instructions and data can be accessed. This caching of instructions greatly speeds up the working of the CPU.
Caches are of two types: i for *instruction* and d for *data* and they are also placed in a hierarchy from L1, L2, ... , where L1 is the fastest and most expensive category and they get slower and cheaper as we go down.

## The compilation process

[tutorialspoint page on the same](https://www.tutorialspoint.com/compiler_design/compiler_design_overview.htm)
