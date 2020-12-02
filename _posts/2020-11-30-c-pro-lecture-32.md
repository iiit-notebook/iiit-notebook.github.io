---
title: C Pro Lecture 32
author: Pratyaksh Gautam
code: cs1.101
number: 32
---

## Organising larger programs into multiple files
While working on large projects, we may want to organise our program into multiple files. For example, we might want to store all our helper functions in one file, all our preprocessor macros and our main program in another.  
Suppose we store these in files `helper.c`, `header.h` and `main.c` respectively. Then we can compile our program with
```
$ gcc helper.c main.c
```
We would have to include `header.h` in the whatever files we need those macros to be in as well

### The compilation process for multiple files

`gcc` first creates the object code for both files, we can execute just this step manually by doing
```
$ gcc -c helper.c main.c
```
The `-c` flag tells `gcc` not to run the linker. Now in the working directory we have two object files, `helper.o` and `main.o`.
These compiled objects however are not yet linked. Any references to identifiers that are contained in another file are still inaccessible from one file, since we explicitly did not run the linker.  
We can now link these files with each other by running
```
$ ld helper.o main.o
```

Now all those cross-references get linked together appropriately. The program may still not run however, since we did not link the standard library objects manually, so any references to functions and macros defined in the standard library will not work. The standard libraries would have to be linked manually.

<hr>

When dealing with large projects that have been split and organised into multiple files this way we can face certain issues.

## Implicit declarations

Consider collaborating on a project with another programmer, where you write some helper functions for them, and they write the higher level code using your helper functions.
Suppose `helper.c` contains a function `void readParagraph(int *num_lines, char ***lines)`, which reads a paragraph from `stdin` with certain restrictions and modifies `num_lines` to contain the number of lines.

Now consider that your co-worker knows of the existence of `readParagraph()` but thinks that it returns an `int`, the number of lines, and takes only `***char`, the paragraph strings.
They might write some code like this
```c
#include "helper.c"
...

	int nlines;
	char **paragraph;
	nlines = readParagraph(&paragraph);
...
```

On compilation, it would give them a warning, telling them that `readParagraph()` was **declared implicitly**, but it would still compile. On running the executable however they would get a segmentation fault.  
This would easily be remedied by looking at the source for `readParagraph()` and it's return type and arguments, but in large code bases segmentation faults can happen for numerous reasons.  
This makes it difficult for your co-worker to understand what went wrong.

One way to prevent such issues is to properly prototype your functions.

We create a new file `header.h`, which contains the function prototype for all out helper functions, including `readParagraph()`:
```c
void readParagraph(int *, char ***);
```
and we include this headerfile in `main.c`:
```c
#include "header.h"
```

Now if we were to compile the program, it would give us an error and refuse to compile. It would tell us exactly what the problem is: the function was called with the wrong arguments, and we tried to assign an integer a `void` value.

The advantage that this gives us is that we are immediately told what mistake we made, and do not have to try and figure out why the executable segfaulted. The **explicit declaration** of our function allowed us to catch the incorrect function call at compile time.

## Scoping across files
Another issue we might face is of function name clashes.  
Suppose in our helper function file itself for the ease of our programming we employ a function `print()` in `helper.c`, but there is another function `print()` defined elsewhere which our co-worker uses in `main.c`.  
If we compile the project, all calls to `print()` in `main.c` are now ambiguous, and the compiler gives an error, telling us that multiple definition of functions is illegal.

While one way of solving this is to simply use different function names, it can be difficult to co-operate in such a way that no function name is used twice, and it can also lead to unwieldy, long names which reduce code readability.

Another way of solving this is to locally scope our functions with the `static` keyword.  
In `helper.c`, we can define `print()` as:
```c
static void print()
{
	...
}
```

This tells the compiler that we only want this function to be called within the context of this file. Only functions within `helper.c` can now call `print()`. Functions in `main.c` are not allowed to call it, meaning all `print()` calls there are now unambiguous, referring to the only `print()` function they are allowed to call.

We reduce the scope of the `print()` function in `helper.c` to only calls from that file itself. Thus, we can use the static keyword to "keep the global namespace clean".
