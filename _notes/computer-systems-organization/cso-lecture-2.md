--
title: CSO Lecture 2
author: Pratyaksh Gautam
date: 2021-05-26
code: cs2.201
number: 2
---

## More on ISA

The ISA is an abstraction for the software to interface with the hardware.
Multiple hardware implementations may exist for the same ISA, but as long
as they follow the specification of the ISA, we can build systems on top
of the ISA without having to consider the hardware implementation below it.

The ISA consists of:  
- **Instruction set**, like `ADD`, `SUB`, `MOV` and other elementary operations.  
- **Instruction format**, e.g how `ADD` instruction must be used, which might be `ADD $1 $2`.  
- **Data types** like integers, floating point numbers, and other data structures.  
- **Adressing modes** which talks about the memory management (more on this later).  
- **Exceptional conditions** like "zero flag" etc.  

We prefer a simpler design for the ISA over a more complicated one with lots of instructions.
This makes it easier to implement at the hardware level, and we also try to not have any redundant
instructions in the ISA, since many instructions we might think of can be broken down into simpler instructions.

## A brief history of increase in computing power

- Moore's law
- Multi core processing
- Compact computing

Pentium 4 processor
more complex, has two cores, instruction cache

## Integer Representation
We represent all data in the form of binary in the digital format.

## Virtual Address Space
We need a mechanism to first name all the memory locations that we are able to access.
The virtual address space is everything that is *adressable*, and the physical address space
is the actual *acessible* memory.

The hardware interface establishes a mapping between the virtual addresses and the physical addresses.

In terms of memory access, we have a 2 selectors to select a register, where the data is stored.  
The size of one unit of memory is called a "word" of memory. The word size can be different for different
machines, for example it may be 32 bit.

We represent pointers to memory in the form of data itself, and the number of memory locations
we can address is limited by this, i.e $2^{32}$ addressable memory locations in the case of 32-bit word size.
