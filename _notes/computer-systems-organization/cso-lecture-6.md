---
title: CSO Lecture 6 Notes
author: Pratyaksh Gautam
date: 2021-06-04
code: cs2.201
number: 6
---


## Assembly code

Consider the below simple code in C.

```c
int accum = 0;

int sum(int x, int y)
{
	int t = x + y;
	accum += t;
	return t;
}
```

If we compile it to assembly code with `gcc -O1 -S code.c`,
we get the following.

```asm
sum:
	pushl	%ebp
	movl	%esp, %ebp
	movl	12(%ebp), %eax
	addl	8(%ebp), %eax
	addl	%eax, accum
	popl	%ebp
	ret
```

All these assembly instructions take up different numbers of bytes in the actual
binary encoding, depending on how many arguments they have and how commonly they are used.

### Processor State

The condition code registers can hold information that tell us some of the more crucial
information about the most recent operation, such as if its result was a zero.

### Data formats

For x86 Intel, the term "word" usually refers to 16-bits, with "double words" being 32-bits, and "quad words" being 64-bits.

### Accessing Information - IA32

In assembly, 8 registers are commonly used: `eax`, `ecx`, `edx`, `ebx`, `esi`, `esp`, `ebp`.
The last two of these have specific functions, they are the stack pointer and the frame pointer respectively. The first six are general purpose for the most part.

`eax` points to 32 bits somewhere in the memory, and we can point just to the last half, 16 bits with `ax`. These 2 bytes can be further broken down into `ah` and `al` if we want to access the second last and the last byte.

```
 x x x x x x x x x x x x x x x x x x x x x x x x x x x x x x x x
31                            15             8 7               0
eax                           ax
                              ah              al
```

### Accessing Information - x86-64

In 64-bit architecture, since we have access to 64 bit registers, we have
`rax`, `rbx` etc., whose second halves can be pointed to by `eax`, `ebx` and so on.

We have 16 total registers here, 8 are the same as in 32-bit, and the rest 8 are new general purpose registers, names `r8` through to `r15`.

### Operand specifiers

Many instructions have one or more operands, used as source and destination references.
They can be of 3 types - constant (immediate), register, memory.
