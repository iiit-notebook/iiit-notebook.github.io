---
title: C Pro Lecture 3
author: Pratyaksh Gautam
code: cs0.101
number: 3
---
[The lecture recording](https://youtu.be/Gs_zV1JtXF0)
## Program: Printing a pun
```c
    /* pun.c */
    #include<stdio.h>

    int main(void) {
	printf("To C or not to C: that is the question.\n");
        return 0;
        }
```

The above is a program in C to simply print the given string to the screen. `main` is a compulsory function and `void` is a keyword used here to denote that the function does not take any arguments.
Upon compilation, this file, saved as *pun.c*, gets converted to an executable, *a.out* by default when using gcc.
`gcc pun.c`

**pun.c** (C source) ASCII    == gcc ==> **a.out** (x86-64) Instruction set executable

### Preprocessing

The `#include<stdio.h>` statement tells the preprocessor to include this library so that we can use the `printf` function which is present in this library.
We can see the output after preprocessing by using `cpp pun.c` and the preprocessed output is printed to stdout.
The preprocessor obeys commands that begin with '#' (known as **directives**). In the preprocessed file for pun.c, *pun.i* (which can be created by running `cpp pun.c > pun.i`), we can see on a line that there is a *function type signature*, for the `printf` function.

### Compilation

After preprocessing, the program has to be compiled, which converts it from C source code to machine instructions (object code).
`gcc -c pun.c` creates pun.o, an object file, which is not yet ready for execution.
If we want to see the assembly code, we can do that too by using `gcc -S pun.c -o pun.s`.

### Linking

Before execution, the object file has to be linked to the standard IO library from which it is calling the `printf` function. This is done by the linker. Note that the preprocessed file only contains the function type signature of the `printf` function, and not the actual definition of the function, thus linking is needed in order to run the program.

## Looking at a simple loop

If we write the following C code:
```c
    /* loop.c */
    int main(void) {
        while(1);
    }
```

We end up in an infinite loop. We can look at this simple infinite loop program in greater detail in its assembly form, by running `gcc -S loop.c -o loop.s`.
Here we look into how this program is executed, and on line 14 in the assembly code we see
```asm
    .L2:
	    jmp	.L2
```

This means that at the memory address `.L2` there is a call for a jump statement, which sends the program counter again to `L2` and this is how our infinite loop functions.
And if we compile and execute this program we can take note of something interesting. Opening up a program like `htop` allows us to see that while our program is running, we have a CPU load of 100% on one of our cores!
In fact, if we load more instances of this loop on different terminals, we get more and more cores running at 100%, until we run out of cores, but interestingly, our computer does not crash when this happens.

On my system, I did not even experience any significant lag due to this. This is because the computer is able to appropriately **timeshare** these processes.
The various threads running on this computer are rapidly switched between in order to do this, and this does not make it immune to slowdown. Given enough processes, the computer will start to feel laggy and slow, and eventually will crash.
It is possible to write a shell script to do exactly this, crash the system by running too many processes, and it is known as a **fork bomb**

On bash:
```bash
    bomb() { 
     bomb | bomb &
    }; bomb
```

This defines a function called bomb in bash, and then calls it, and pipes its output to another instance of bomb. The '&' places it in the background so the recursive loop can continue.
This rapidly spawns multiple instances of the bomb process and thus crashes your computer.
[Further reading on the bash fork bomb](https://www.cyberciti.biz/faq/understanding-bash-fork-bomb/)
