---
title: CSO Lecture 13 Notes
author: Pratyaksh Gautam
date: 2021-06-23
code: cs2.201
number: 13
---

## Comparing Instruction Set Architecture paradigms (Complex vs Reduced)

|  CISC	                                      |  RISC                                          |
|  ---                                        |  ---                                           |
| Adopted by Intel                            | Promoted by IBM and ARM family                 |
| Large number of instructions                | Fewer instructions (<100)                      |
| Allow instructions with long execution time | No instruction with long execution time        |
| Variable-length instruction encodings       | Fixed length instruction encodings             |
| Multiple formats for specifying operands    | Simple addressing formats                      |
| Implementation artefacts abstracted away    | Implementation artefacts exposed to programmer |
| Condition codes. Special flags set as side  | No condition codes. Explicit test instructions |
| effects of instructions.                    | store the test results in normal registers     |

## Y86 ISA

It is a simplified version of the IA32 instruction set, which applies some of the principles of
RISC. It has fewer data types, instructions etc. Y86 only allows 4 byte integer operations.

In the context of Y86, we use "word" to mean 4-bytes, since it is the only size we will operate on.

Registers available are, `%eax`, `%ebx`, `%ecx`, `%edx`, `%esi`, `%edi`, `%esp`, `%ebp`.

It also has condition codes, ZF, SF, OF, a program counter, and a program status code, and of course
a memory.

### Assembly code

The numbers in the brackets are 4 bits each, representing the bit-level encoding of the instructions.

- `halt` [ 0 0 ] - stops instruction exec, and sets status code to HLT.
- `nop` [ 1 0 ] - idle state, no operation
- `rrmovl` rA, rB [ 2 0 rA rB ] - move from register A to register B
- `irmovl` V, rB [ 2 0 F rB V ] - move immediate value V to register B
- `rmmovl` rA, D(rB) [ 4 0 rA rB D ] - move from register A to memory address at rB with offset D
- `mrmovl` D(rB), rA [ 5 0 rA rB D ] - move from memory address at rB with offset D to register A
- `OP1` rA, rB [ 6 fn rA rB ] - For arithmetic operations
- `jXX` Dest [ 7 fn Dest ] - different kinds of jump instructions, to destination

Thus some instructions are just 1 byte long, but those that require operands have longer encodings.
There is no support for the second index register or scaling, only offsets are allowed.

#### Arithmetic Codes
The `fn` mentioned in `OP1`
`addl` - 0
`subl` - 1
`andl` - 2
`xorl` - 3

#### Jump Codes
the `fn` mentioned in `jXX`
`jmp` - 0
`jle` - 1
`jl`  - 2
`je`  - 3
`jne` - 4
`jge` - 5
`jg`  - 6

#### Conditional move instructions

#### States / Exceptions
| Name | Meaning                          |
|---   |---                               |
| AOK  | Normal operation                 |
| HLT  | `halt` instruction encountered   |
| ADR  | Invalid address encountered      |
| INS  | Invalid instruction encountered  |
