---
title: C Pro Lecture 1
code: cs0.101
number: 1
---
## Computing system = Hardware + Software

Every computing system is composed of both hardware and software, for eg: applications (software) running on a smartphone (hardware).
Computing systems can be run in parallel, through large networks of many computers, or they can also be run as a single computer. Our focus in this course will be on programming on a single computer.

## Memory model

- Logically, memory can be thought of as a *linear array of bytes*, though its physical implementation can be organised in different ways)
- Each byte is a sequence of 8 bits
- **RAM** - Stands for *Random Access Memory*. It is a volatile form of memory where the access time for any byte is uniform. It does not matter what byte we try to access, it will be retrieved in the same amount of time as any other byte.

The memory is stored in this linear array form, where each memory cell has an address (for example 0x0, 0x1, 0x2, ... ), and the memory controller allows the CPU to access individual bytes in the memory.

## Execution model

- The CPU contains a **PC (Program Counter)** which has an instruction address in it. The instruction present at that address in the memory is then retrieved, and this is known as *"fetching an instruction"*.
- After instruction fetch, that instruction is decoded. The instruction is represented in binary and the CPU interprets what the instruction is supposed to tell the computer to do.
- Then the instruction is executed accordingly. Three types of instructions are:
    - Computation (addition, subtraction, etc.)
    - Control (branch, call etc.)
    - Read/Write/Modify data

Control instructions like branch allow us to jump back to a previous address.

For the sake of simplicity, let us assume that an instruction has a length of 4 bytes. Then, after an instruction is executed, the program counter increments by 4 bytes (the instruction length). 
The CPU itself only calls for the first address where the instruction begins. The memory controller then retrieves the whole instructions (4 bytes in our case) and then sends it to the CPU.

## What is a program?

Simply put, a program is a *sequence of instructions along with the necessary data.*

The data can be:
- part of the program
- retrieved from elsewhere (as input)
- generated during program execution (as output)

## Executing a program

1. Initially, instructions and date of a program are present on the hard disk
2. They are then loaded into the main memory.
3. After this, control is transferred to the CPU to execute the program.

In the OS kernel, there is a 'loader' which performs this function of preparing the program to be run and transferring control to the CPU.
_So then who loads the loader?_ 
It is the job of **BIOS** *(Basic Input/Output System)*, the first software to run when the computer is turned on. The BIOS loads up the bootloader, which in turn eventually loads the operating system. From then on the OS kernel handles such operations. 
The BIOS is stored on non-volatile flash memory, and is only used once (during startup), then the OS kernel takes over.
