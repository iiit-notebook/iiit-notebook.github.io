---
title: C Pro Lecture 9
code: cs0.101
number: 9
---
## Associativity

Subtraction is left associative in C.
```c
printf("%d", 1 - 2 - 3) // outputs (-4) not 1
```

## Operators and Precedence

C has two types of increment operators, postfix and prefix. Postfix operators perform the increment/decrement after using the value, whereas prefix operators perform the increment/decrement before using the values.
```c
i = 10;
printf("%d", ++i) // prints 11, i is now equal to 11
printf("%d", i++) // prints 11, i is now equal to 12
```

Note that unary increment operator has greater precedence than the binary multiplication.
```c
int i = 2, j;
j = i * i++;
printf("%d %d", i, j); // prints 3, 6
```

We can even do multiple assignments in the same expression. We must be very careful when doing this though, since it is not recommended due to how it affects the readability of the code.
```c
int i, j = 1, k;
k = (i = j+1) + 1;
printf("i = $d, j = $d, k = %d\n", i, j, k); // Outputs i = 2, j = 1, k = 3
```

## Flow of Control

In C, zero is treated as false, and any non-zero value is treated as true.
We can use if statements to make our code run according to certain logical expressions, and run different pieces of code accordingly.

 ```c
if(condition) {
    // some code here
}
else {
    // some alternate code here
}
```
The curly brackets are only required when we have multiple statements inside the if block. If we have a single statement, we can omit it.

A convenient datatype for storing these true/false type values is `bool`, defined in `<stdbool.h>`.
`bool = true;` is a valid statement, since the keywords `true` and `false` are defined in the headerfile.

Let us look at an example where there is some ambiguity, known as an dangling-else statement.
```c
#include<stdio.h>
#include<math.h>

main()
{
    float x, y, result;
    printf("Enter x and y: ");
    scanf(%f %f, &x, &y);
    if (y != 0)
	if (x >= 0) {
	    result = sqrt(x) / y;
	    printf("Result: %f\n", result)
	}
    else
	printf("Error: y is equal to 0\n");
}
```

Here if we input `12 0`, the initial condition is false and so the code nested in that block is not executed, and we expect the else block to now be executed, but it is not.
We get no message. This is because the else statement is by default associated with the last if statement written.
We can of course remove this ambiguity by adding curly brackets appropriately to show which else statements belongs where.


```c
#include<stdio.h>
#include<math.h>

main()
{
    float x, y, result;
    printf("Enter x and y: ");
    scanf(%f %f, &x, &y);
    if (y != 0) {
	if (x >= 0) {
	    result = sqrt(x) / y;
	    printf("Result: %f\n", result)
	}
    }
    else
	printf("Error: y is equal to 0\n");
}
```

Now the else statement unambiguously belongs to the outer if condition.
