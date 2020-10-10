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
    printf("\nThemax is: %d\n", max);

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

We could've been even stricter about the negative numbbers if we wanted to and displayed a warning if negative numbers are input.
```c
    if(inp < 0)
	break;
```
Now we would completely exit the loop if we encountered a negative number and just print the sum up till now.
We could've printed a warning too if we wanted to.

## `goto` statement

`goto` statement

## `assert()` function
