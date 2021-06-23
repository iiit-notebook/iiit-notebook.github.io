---
title: CSO Lecture 10 notes
author: Yash Mehan
date: 2021-06-14
code: cs2.201
number: 10
---

## Jump Instruction Encodings

Some of the most commonly used encoding is relative to the program counter (PC Relative). This means that the assembler sees how many bytes away from the program counter, the destination label of `jmp` is, and writes that onto the .o file. This distance, or "offset" can be 1 byte long, (i.e. a `jmp` which spans 127 bytes) or 2 bytes long or 4 bytes long.

A second method is to give an absolute address, using 4 bytes to directly specify the destination.

The assembler and linker select appropriate methods when required.

 The following is an assembly file.

```
		jle .L2 
.L5: 
    movl %edx, %eax
    sarl %eax
    subl %eax, %edx
    leal (%edx,%edx,2), %edx
    testl %edx, %edx
    jg .L5 
.L2: 
    movl %edx, %eax
```

This is the disassembly of the object file:

```
8: 7e 0d        jle 17 <silly+0x17> 
a: 89 d0        mov %edx,%eax 
c: d1 f8        sar %eax
e: 29 c2        sub %eax,%edx
10: 8d 14 52    lea (%edx,%edx,2),%edx
13: 85 d2       test %edx,%edx
15: 7f f3       jg a <silly+0xa> 
17: 89 d0       mov %edx,%eax
```

When the instruction at address `8` is being executed (this the addressing relative to the first instruction of the program), the program counter has `a` stored in it. `7e` is the opcode for `jle` and `0d` is the offset, i.e. the number of bytes to be jumped. `a` + `0d` = `17` in base 16. So this `jle` will set the program counter, to address `17` which is `mov %edx, %eax` . This is exactly what was intended in the assembly program as well.

Similarly for backward jumps, the offsets will have a value, which when represented in binary will have its MSB as 1, i.e. a negative number.

The following is the disassembled version of the program after linking:

```
804839c: 7e 0d          jle 80483ab <silly+0x17>
804839e: 89 d0          mov %edx,%eax
80483a0: d1 f8          sar %eax
80483a2: 29 c2          sub %eax,%edx
80483a4: 8d 14 52       lea (%edx,%edx,2),%edx
80483a7: 85 d2          test %edx,%edx
80483a9: 7f f3          jg 804839e <silly+0xa>
80483ab: 89 d0          mov %edx,%eax
```

After linking, the addresses of the instructions are changed to absolute addresses. When the instruction on `804839c` is being executed, the program counter stores `804839e`, and the offset of `0d` causes the program counter to update to `804839e + 0d` which is `80483ab`, which is again what the original assembly file intended to do.

## Conditional moves

The idea of conditional moves is to avoid writing one separate branch just for the sake of `mov`-ing. 

```c
if( condition ){
	//then-block
} else{
	//else-block
}
```

One can create a label for `then-block`, then `jmp` back to the if condition, then create another label for `else-block` and `jmp` back.

Consider a function to find the absolute difference between two numbers.

An idea to avoid using `jle`, `jg` etc is to pre-calculate both `x-y` and `y-x`, store one of them, say, `x-y` as the return value. Then check if `x<y` then `mov` into `%eax` the `y-x` value. 

```
movl 8(%ebp), %ecx              # Get x into %ecx
movl 12(%ebp), %edx             # Get y into %edx
movl %edx, %ebx                 # Copy y
subl %ecx, %ebx                 # Compute y-x
movl %ecx, %eax                 # Copy x
subl %edx, %eax                 # Compute x-y and set as return value
cmpl %edx, %ecx                 # Compare x and y
cmovl %ebx, %eax                # If <, replace return value with y-x
```

In the instruction `cmovl`, the `l` stands for less than, not `long`. Similar to the `jmp` family, which had `jl`, `jg`, `je`, `jne`, `jge`, etc. `cmov` family has the exact same suffixes and similar logic. `cmov` instructions check work upon the values in those very flags as `jmp` instructions do. Observe that we have a redundancy here, we are calculating both `x-y` and `y-x`. Although since subtraction isn't much of an expensive process, it doesn't make much difference, but had there been calculation intensive branches, then performing both of them only to discard one at the end would be inefficient.

## Pipelining and `jmp`

For successful execution of each instruction, we can roughly say the following steps need to be completed:

1. Fetch the instruction from memory
2. Decode
3. Load operands
4. Execute the instruction
5. Save output
6. Updating the program counter

A common technique to speed up processing is doing these steps parallelly for each instruction, much like an **assembly line in a factory**. For example, while say, instruction 42 is undergoing stage 6, instruction 43 is undergoing stage 5, instruction 44 is undergoing stage 5 etc., rather than letting instruction 42 to go through stages 1, 2, ... 6; then instruction 43 go through 1, 2... 6. 

For the most part, this technique helps in quick execution of instructions because otherwise most of the modules which fetch, decode etc. will be idle. Consider the following scenario:

```
fetch    Decode    Load OP    Exec    Save Output    Update PC
-----    ------    -------    ----    -----------    ---------
47       46        45         44      43             42    
```

Suppose instruction 44, which is under execution, asks for `jmp`ing to an instruction, say 100. Then this queue, of 47, 46, 45 has to be cleared, and instruction 100 has to be put in the Fetch stage.

```
fetch    Decode    Load OP    Exec    Save Output    Update PC
-----    ------    -------    ----    -----------    ---------
100      ~         ~          ~       44             43
101      100       ~          ~       ~              42
102      101       100        ~       ~              ~
```

Not only the clearing is wasteful, but these `~` these blank spots in the pipeline are causing the processing to slow down, because the modules which undertake these steps are idle again. This is how`jmp` slows down the execution of a program. `cmov` s avoid this issue. There is a tradeoff to make, either to do redundant calculations, some of which would have to be discarded, or have idling spots in the pipeline. This is the compiler's job to evaluate which one is most efficient.

## Error Conditions

Given a pointer, a function which returns the value stored at the location pointed, and 0 if the pointer is `NULL`, using `cmov` isn't safe because when the pointer is indeed `NULL`, the code will segfault at line 1.

```
movl (%edx), %eax
testl %edx, %edx
movl $0, %edx
cmove %edx, %eax
```

Were we using `jmp`, we'd have to first `testl` . If the pointer turned out to be `NULL` we wouldn't have to dereference the `%edx`, and saved ourselves from segfaults.
