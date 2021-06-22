---
title: CSO Lecture 9 notes
author: Yash Mehan
date: 2021-06-11
code: cs2.201
number: 9
---

## Condition Codes

Usually the program counter increments by 1 instruction. Now we wish to modify the flow of control based on certain conditions. There is a set of single bit flag registers which describe the status of a recent arithmetic operation. Whatever the conditions evaluate to, the result is updated in one of these flag registers; and based on content of these flag registers, the flow can be directed.

The `FLAGS` register has 16 bits, where each bit serves as the storage for the result of different conditions/operations. The successors of `FLAGS` is `EFLAGS`, which is 32 bits wide, and `RFLAGS`, which is 64 bits wide.

The commonly used flags are: 

- `CF` Carry flag: used to detect overflow in operations with unsigned numbers
- `OF` The Overflow Flag is set to 1 when 2's complement signed numbers overflow: both positive overflow and negative.
- `ZF` Zero flag if the most recent operation yielded a 0, then it is set to 1. Also used in conditional branch instructions, which alter control flow based on previous instruction results.
- `SF` Sign Flag: if the most recent operation yielded a negative value, then `SF` is set to 1. More generally, `SF` takes the value of the MSB of the value yielded. Incase it is negative, it will have a 1 as its MSB, and if non-negative, then a 0.

Example: 

- Suppose we have `t = a+b;` in C.
    - if unsigned interpretation of `t` evaluates lesser than unsigned interpretation of one of the operands, then `CF` is set 1.
    - if `t` becomes 0 after the addition, then `ZF` is set 1.
    - if `t` becomes negative after addition then `SF` is set 1.
    - `OF` is set to 1 when both following conditions are fullfilled:
        - `a` and `b` are of the same sign
        - `a` and `t` are of different sign (talking about the sign is meaningful when we interpret `t`, `a`, `b` as signed 2's complement)
- the `lea` instructions won't change any of these flags.
- for `xor` there will never be any carry generated, not will there be any overflow, so `CF` and `OF` are both set to 0.
- for shifting instructions, the `CF` will be the value of the bit last shifted out, but `OF` is set to 0.
- `inc` and `dec` do modify the `OF` (and rightly so), but not `CF`

## `cmp`

`cmp` can set all these four flags. It merely subtracts the operands passed to it and on the basis of the difference updates the flags, but doesn't update/modify the content stored at the registers/locations which were passed as operands. By difference, we mean

```
cmp left_op, right_op # means right_op - left_op
```

- if the both are equal, `ZF` is set to be 0. Otherwise:
- `ZF` becomes 1
- `SF` is 1 if the difference is negative, `SF` is 0 if the difference in positive. It is still possible for difference to be negative when the first number is greater than the second. This because of overflow.
- Considering 2's complement interpretation of the bits of the numbers, `OF` is set to 1 if there is an overflow, otherwise 0.
- Considering the bits of the numbers as unsigned, the `CF` is set to 1 if there is a carry. Why these flags are necessary, will be revealed in the following parts of text.

## Using Condition Codes

- Can set 8 bits depending on some combination of these registers, using the `set` family of instructions
- make a conditional jump
- make conditional move

## Accessing Condition Codes by `set` family

You just ran an instruction for comparing two operands and and you need to check the result. i.e. if one of the operands is $>, \geq, <, \leq, =, \neq$ the other operand. Or maybe if the instruction gave a negative output. `D` is a 1 byte location in memory, or a 1 byte register `%al` or `%bh` etc.

- `sete D` will set all 8 bits of D the same as `ZF`
- `setne D` will set all 8 bits as NOT of `ZF`

The following instructions interpret the bits to be in 2's complement form

- `setg D` sets D as 1 if `right_op > left_op`. Works by `(~(SF ^ OF)) & (~ZF)`
- So, `setle D` should work as `(SF ^ OF) | ZF`
- `setl D` works as `(SF ^ OF)`
- and so `setge D` should work as `~(SF ^ OF)`

**Example**: consider two 3 bit numbers, `b` which has `100` and `a` which is `010`. Interpreting them as signed, `b` is -4, and `a` is 2. So we should get a `true` for `b <= a` and `b < a`.

Doing `b - a` which is adding `100` and `110` we get `010`, and `1` as an overflow. Now,

- `ZF` = 0
- `SF` = 0
- `OF` = 1

- `(SF ^ OF) | ZF` is `(0 ^ 1) | 0` which is `1`.
- `(SF ^ OF)` is `(0 ^ 1)`which is `1`.

We can interpret `100` and `010` as unsigned and draw a similar analogy.  Here the `CF` will be 0.

## `jmp`

- `jmp mylabel` will jump to `mylabel` unconditionally
- `jmp *operand` will jump to the address which (content at `operand`) bytes ahead of the current instruction
- `je`, `jne`, `js`, `jg`, etc. which work the same as `set`, except they update the program counter to the operand if the conditions evaluate to be true.

Two common encodings: Relative, where `jmp` is given how many bytes to skip to the next instruction, the other is absolute, which gives `jmp` a 4 byte long absolute address.
