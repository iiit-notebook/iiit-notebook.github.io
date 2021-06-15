---
title: CSO Lecture 8 notes
author: Yash Mehan
date: 2021-06-09
code: cs2.201
number: 8
---

## Arithmetic Operations:

Suffix `l` needs to be added to the following instructions

- Unary:
    - `inc d`  C equiv: `d++;`
    - `dec d` C equiv: `d--;`
    - `neg d` C equiv: `d = -d;`
    - `not d` this is bitwise `NOT`, not to be confused with logical NOT, flips each bit individually, does not effect the `FLAGS`. C equiv: `d = ~d;`
- Binary:
    - `add s, d` C equiv: `d = d + s;`
    - `sub s, d` C equiv: `d = d + s;`
    - `imul s, d` C equiv: `d = d * s;`
    - `xor s, d` C equiv: `d = d^s;`
    - `or s, d` C equiv: `d = d | s;`
    - `and s, d` C equiv: `d = d & s;`
- Shift Operations
    - `sal k d` arithmetic shift left the bits of `d` by `k`
    - `shl k d` exactly same as `sal` created only because there were arithmetic and logical analogs version of shift right
    - `shr k d` logical right shift: The MSB in the original number might be 0 or 1, irrespective,  0s are pushed in from the MSB side.
        - `sar k d` Arithmetic right shift: If the MSB in the original number is 0, then 0 is pushed in, if MSB is 1, then 1 is pushed in.
    - in these instructions, `k` can take the value
        - of a constant (aka immediate) e.g. `$0x4` or
        - from a register e.g `%eax` or
        - from the one-byte register `%cl` (the lowest significant byte of `%ecx`)

## Multiplication with overflows

- for signed "full" multiply: `imull s` one of the multiplicand is `s`, the other will be `%eax`.  After multiplication, the most significant 32 bits will be stored in `%edx` and the lower 32 significant bits in `%eax`. Notation: $\textbf{R[}$ `%edx` $\textbf{]:R[}$ `%eax` $\textbf{]} \leftarrow \textbf{S} \times\textbf{R[}$ `%eax` $\textbf{]}$
- Similarly for unsigned full multiply: `mull S`. Does the same thing.
- `S` can be a constant (aka immediate)  or from a register e.g. `%ebx` or `8(%ecx)` etc.

## Division and `cltd`

No args. `c`onvert signed `l`ong `t`o signed `d`ouble long. (basically a quad). Will take the value stored in `%eax` and signextend it, and store the most significant 32 bits in `%edx` and least significant 32 bits in `%eax`. Signextending means setting all bits in `%edx` to the sign bit of `%eax`

Notation: $\textbf{R[\%edx]:R[\%eax]} \leftarrow signextend(\textbf{R[\%eax])}$

- Division instructions follow the idea, where the quotient is stored separately, in `%eax` and remainder in `%edx` The arg `S` that is passed, is the divisor. the dividend is the number made from $\textbf{R[\%edx]:R[\%eax]}$. A usual 32 bit number can be made to be 64 bit big moving into `%eax` then calling `cltd`
- `idivl S` for signed divide, functioning as above
- `divl S` for unsigned divide, same functioning as above.

