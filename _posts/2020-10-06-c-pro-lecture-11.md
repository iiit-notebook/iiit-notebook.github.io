---
code: cs0.101
author: Pratyaksh Gautam
title: C Pro Lecture 11
number: 11
---

## Loops

A `while` loop simply checks the expression passed to it. It executes the code given repeatedly, checking the condition before every loop.
```c
#include<stdio.h>

void main(void)
{
    int n;
    printf("Enter a number whose table you want printed: ");
    scanf("%d", &n);
    int i = 1;
    while(i <= 10) {
	printf("%d x %d = %d\n", i, n, i*n);
	i++;
    }
}
```

The above code executes till `i` becomes greater than 10.

`while` loops are straightforward, but sometimes `for` loops can be more convenient, or faster to write.
They follow the syntax:  
```c
for ( initialization; check condition; updation ) {
    // some code here
    }
```

So if we were to write the same `while` loop as before using the `for` loop syntax, we would have:
```c
for(int i = 1; i <= 10; i++) {
    printf("%d x %d = %d\n", i, n, i*n);
}
```

There is also another kind of a loop known as a `do while` loop. It can be very handy in certain situations due to its readability. For example

```c
int main()
{
    int digits = 0, n;
    printf("Enter a nonnegative integer: ");
    scanf("%d", &n);

    do {
	n /= 10;
	digits++;
    } while (n > 0);

    printf("The number has %d digits.\n", digits);

    return 0;
}
```

The `do while` loop also has the property that it is guaranteed to execute at least once. Since it is an *exit controlled loop*,
it checks the condition after one execution of the loop, instead of before one execution.
