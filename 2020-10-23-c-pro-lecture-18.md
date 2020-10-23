---
title: C Pro lecture 18
author: Pratyaksh Gautam
code: cs0.101
number: 18
---

## More on functions
### Linear Congruential Generator
```c
/* LCG: X_(n+1) = (aX_n + c) mod m */
#include <stdio.h>
#include <time.h>

#define a 1103515245
#define c 12345
#define m (1 << 31) // bit shifting, equivalent to 2^31

unsigned int X;

void srand(unsigned int seed)
{
    X = seed;
}

unsigned int rand()
{
    X = (a * X + c) % m;
}

main()
{
    srand(time(0));
    printf("%u\n", rand());
}
```

Here we have emulated the functioning of the standard C functions to generate pseudo-random numbers, with our own *linear conventional generator*.
The `srand()` is to seed our function, and `rand()` is our RNG.

### A bit more about bit-shifting.

`1 << 31` is an expression equivalent to $2^31$. The `<<` operator, is the bitwise left-shift operator.  
Consider the binary representation of the number 1, it will also be just `1`. `<< 31` shifts the bits in the binary representation of the number by 31 places,
effectively turning it into `10000000000000000000000000000000`, or $2^31$.

## Scope and lifetime of functions

```c
#include <stdio.h>

int max(int a, int b)
{
    if (a > b)
        return a;
    else
        return b;
}

float average(int a, int b)
{
    float average;

    average = (a + b)/2;

    return average;
}

main()
{
    int A, B;

    printf("Enter numbers A and B: ");

    scanf("%d %d", &A, &B);

    printf("Average: %f\n", average(A, B));
    printf("Maximum: %d\n", max(A, B));
}
```

In the above code, the function `average()` itself has a variable `average`. This variable is limited to the **scope** of the function, that is to say it cannot be accessed outside this function.[^1]  
As soon as we reach `return average;`, the function exits and returns this value, and the variable `average` no longer exists; its lifetime is said to be over.

The same thing actually happens with the `main()` function too, all the variable in it also exist within the scope of `main()`, and as a result, cannot be accessed from other functions.

### Global variables

Thankfully there is a **global** scope as well, variables from which can be accessed from anywhere in the program.

```c
#include<stdio.h>

int x = 10, y = 20;

void print_x(void) {
	printf("%d\n", x);
}

void print_y(void) {
	printf("%d\n", y);
}

int main(void) {
	print_x();
	print_y();
	return 0;
}
```
The above code demonstrates us declaring and initializing the variables `x` and `y` in the global scope, and using them without issues in two separate functions. Clearly global variables can be very useful.


[^1]:
Note: In fact we have an interesting case here, since the name of the variable is the same as that of the function, so if we were to call the function in that scope, we wouldn't be able to.  
The scope already has a float variable `average` masking it and since they both have the same identifier, the function cannot be accessed and is said to be **masked**.
