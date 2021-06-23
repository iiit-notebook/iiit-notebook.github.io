---
title: CSO Lecture 11 notes
date: 2021-05-19
author: Yash Mehan
code: cs2.201
number: 11
---
## Loops

A plan for a loop. For, while, do-while all are follow similar implementation.

```
init expressions
t = test expression
if(!t)
	goto done
loop:
body
update expression
if(t)
	goto loop
done:
```

## Switch statements

to check a variable against multiple cases, which are constants themselves. `switch` doesn't check against each statement sequentially. Maintaining an array of labels where to jump and looking up that array to `jmp` to location without actually checking other conditions. This works efficiently if the cases are close, but we need a hash table if cases are far apart. [request clarification] 

**Example:**

```c
switch(n){
case 100:
	result = 100;
	break;
case 102:
	result = 102;
case 103:
	result = 103;
	break;
default:
	result = 0;
}
```

To get an idea of how it is implemented in assembly, consider this C snippet:

```c
static void* jumptable[4] = {&&label_A, &&label_default, &&label_B, &&label_C};
//&& is GCC-sepecific sytanx to get the address of labels. unary operator
unsigned index = n - 100; 
int result;
if(index > 3){goto label_default;}
goto *(jumptable[index]);

//`*` is necessary here because the array stores the address of labels. 
//goto doesn't need the address of the label, but the label itself.
//hence the dereferencing 

label_A:
	result = 100;
	goto done; //notice the `done` label here
label_B:
	result = 102; //notice the absence of `goto done` here
								// and the fact the subsequent lines will be executed
label_C:
	result = 103;
	goto done;
label_default:
	result = 0;
done:
	return result;
```

 Assembly snippet on how to set up a jump table, assume `n` is already `mov`'d into `%eax`

```c
subl $100, %eax    # n = n-100 
compl %6, %eax     # compare 6 with n
jge label_default
jmp *jumptable( , %eax, 4)
```

where `jumptable` is an array defined in `.rodata` section

```c
.section .rodata
.align 4
.jumptable
.long label_A
.long label_B
.long label_C
```
