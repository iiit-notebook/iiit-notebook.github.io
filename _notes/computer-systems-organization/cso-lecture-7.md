---
title: CSO Lecture 7 notes
author: Pratyaksh Gautam
date: 2021-06-07
code: cs2.201
number: 7
---

## Operand specifiers

Suppose the initial state of memory and registers looks like the following:
```
Memory          Register

Addr   Val      Reg   Val
-----------     ----------
0x100  0xFF     %eax  0x100
0x104  0xAB     %ecx  0x1
0x108  0x13     %edx  0x3
0x10C  0x11

```

Now if we were to execute one of the following instructions, (not sequentially, just any one instruction),
we would get:

1. `movl $0xFFFF %eax`
Store the value `0xFFFF` in `%eax`

2. `movl %eax %edx`
Copy the value of register `%eax` into `%edx`

3. `movl 0x108 %edx`
Copy the value at memory address `0x108` into `%edx`

4. `movl (%eax) %edx`
Interpret the value of `%eax` as a memory address, and copy the value at that address to `%edx`

5. `movl 0x8(%eax) %edx`
Interpret the value of `%eax` as a memory address, offset it by `0x8`, and copy the value at this calculated address to `%edx`

6. `movl (%eax, %ecx) %edx`
Interpret the value of `%eax` as a memory address, offset it by the value at `%ecx`, and copy the value at this calculated address to `%edx`

7. `movl 0x100(%eax, %ecx, 0x1) %edx`
Interpret the value of `%eax` as a memory address, offset it by the value at `%ecx` times the constant `0x1`,
offset this further by the constant `0x100`, and finally copy the value at this calculated address to `%edx`

## Data Movement Instructions

The most basic data movement instructions are the following:  
- `movb` - move byte  
- `movw` - move word  
- `movl` - move double word  
- `movq` - move quad word (64-bit only)  

When copying from a smaller field to a larger field, we have to take care of the sign
and padding with either 0's or 1's appropriately. For this we have the following:

- `movsbw` - move sign-extended byte to word  
- `movsbl` - move sign-extended byte to double word  
- `movswl` - move sign-extended word to double word  

- `movzbw` - move zero-extended byte to word
- `movzbl` - move zero-extended byte to double word
- `movzwl` - move zero-extended word to double word

For unsigned copying, `movzbq` `movzwq` exist only, since `movl` already copies with zeros for padding.
