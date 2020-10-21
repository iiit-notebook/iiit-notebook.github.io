---
title: C Pro Lecture 17
author: Pratyaksh Gautam
code: cs0.101
number: 17
---

## Functions

Up till now, all our C code has been dealing with a single function, i.e. `main`.
Functions in general take in some input in the form of **arguments** or **parameters**, run some code, and return some data as a **return value**.
Functions have obvious value in modularity and abstraction.

```c
int main(void)
{
	// ... some code here

	return 0;
}
```
Functions follow this general structure as shown above.
The `int` before the name of the function tells us that this function will return an integer when it is done.
The `void` in parentheses tells us that the function does not accept any parameters or arguments.
And finally we have a `return` statement, with `main` returning a value of `0` upon exiting.

### Modularity

```c
#include <stdio.h>
#include <stdbool.h>

bool isDivisor(int N, int d)
{
	if (N % d == 0)
		return true;
	else
		return false;
}

int main(void)
{
	int d, n;

	printf("Enter N: ");
	scanf("%d", &n);

	for(d = 2; d <= n; d++)
	{
		if (isDivisor(n, d) == true)
			break;
	}

	if (d < n)
		printf("%d is divisible by %d\n", n, d);
	else
		printf("%d is prime\n", n);

	return 0;
}
```

In the above code, we have separately defined a function `isDivisor` which gets called when we want to know whether a number is a divisor of another or not.  
By defining this function separately we get the advantage that we can focus on the different problems one at a time; first we can focus on implementing a method to check the divisor, and then once we have it,
we write a function for it and after this we can use this function for the purpose of solving our larger problem without having to think about how to check the divisor each time.

Once we have implemented `isDivisor`, we can treat it as a black box if we want. We only need to care about the input and the output, this is the idea of **abstraction**.

## backtrace in gdb

gdb has a very useful command that allows you to see the backtrace, or the *function call stack* by typing `backtrace` or `bt` for short.
```
(gdb) bt
#0  isDivisor (N=10, d=2) at test.c:8
#1  0x00005555555551d6 in main () at test.c:23
```

The above messages from gdb tells us that the `isDivisor` function is called with the parameters N = 10, and d = 2, and it also tells us that the function was called by `main` at line 23.  
This information is very helpful in debugging large programs, with nested function calls and various return types all over the place.
