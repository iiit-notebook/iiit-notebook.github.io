---
name: C Pro Lecture 12
author: Pratyaksh Gautam
code:  cs0.101
number: 12
---
## Program to find the max integer in a series

```c
#include<stdio.h>
#include<limits.h>

int main(void)
{
	int n, max = INT_MIN;

	printf("This program finds the maximum of a series of integers.\n");
	printf("Enter integers to evaluate (0 to terminate): ");
	scanf("%d", &n);
	while(n != 0) {
	if (n > max)
		max = n;
	scanf("%d", &n);
	}
	printf("\nThe max is: %d\n", max);

	return 0;
}
```

The above program is a bit buggy, in the sense that if we immediately enter 0, we get `INT_MIN` as the output.

While testing this program we can also use a shell trick help things out a bit
```bash
$ ./a.out < input.txt
```
and keep all the input in input.txt, so we don't have to type it out each time.

## Program to sum a series of integers

```c
#include<stdio.h>

main()
{
	int n, sum = 0;
	printf("This program sums a series of integers.\n");
	printf("Enter integers: ")

	while (scanf("%d", &n) == 1)    // Check that printf is able to properly take input
	sum += n;

	printf("\nThe sum is: %d\n", sum);
}
```

## Program to take the sum of positive integers

```c
#include<stdio.h>

main()
{
	int inp, sum = 0;

	while (scanf("%d", &inp) == 1)
	{
	if (inp < 0)
		continue;
	sum += inp;
	}
	printf("The sum is %d\n", sum);
}
```
The `continue` statement simply skips the *current* iteration of the loop, continuing on to the next iteration. As a result, we do not add negative numbers

We could've been even stricter about the negative numbers if we wanted to and displayed a warning if negative numbers are input.
```c
	if(inp < 0)
	break;

Now we would completely exit the loop if we encountered a negative number and just print the sum up till now.
We could've printed a warning too if we wanted to.

## `goto` statement

The `goto` statement allows us to traverse the C code arbitrarily, by defining points in the code we can jump to anytime.
While sometimes quite useful, the us of `goto` statements is often discouraged unless the programmer know what they're doing since it can mean that the code is harder to read and comprehend due to it's non linear nature.

```c
int n;
L1:
	scanf("%d", &n)
	printf("You have entered %d!\n", n)
	goto L1;
```

The above program essentially works in the exact same way as an infinite loop. We simply declared a point `L1` in the code, right before the `scanf` function,
then we used `goto L1` to tell the compiler that we wanted the code to be read again from `L1`. Of course `goto` can be used for a lot more than this,
it allows us to reach arbitrary (and perhaps otherwise unreachable) sections of our code.

## `assert` function

Assertions can be used by the programmer to test their code for certain assumptions or conditions which are essential to the functioning of their program.
If the expression given as an argument to `assert` evaluates to false, then the program exits and tells us the line where the assertion failed.
We must also use the headerfile `assert.h`.
```c
int n = 7;
assert(n == 9);
```

When we compile and run the above code, we get:
```
a.out: test.c:7: main: Assertion `n == 9' failed.
```
This can be very helpful in debugging.
