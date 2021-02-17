---
date: 2020-09-23
title: C Pro Lecture 6
author: Pratyaksh Gautam
code: cs0.101
number: 6
---
[The lecture recording](https://youtu.be/a3AwIqBNKqk)
## More on printf

`printf` function also returns a value, in addition to printing its arguments to `stdout`. It returns the count of the number of the characters it printed. For example:

```c
#include<stdio.h>

int main()
{
    int length, n;
    n = 10;
    length = printf("n is %d\n", n);
    printf("We just printed %d characters to the screen\n", length);
    return 0;
}
```
The above code prints the following output:
```
n is 10
We just printed 8 characters to the screen
```
We printed 8 characters, because the *newline* character is also counted by `printf`.

`printf` also offers greater capacity for us to control the way the output is formatted using placeholders. We already know that in the previous piece of code we used a `%d` as a placeholder for an integer. 
We also have available other placeholders, or *flags*, for different data types such as `%f` for float, `%e` for scientific notation etc.

Take for example the following code:
```c
#include<stdio.h>

int main()
{
    int i = 100;
    printf("i = %d\n", i);
    printf("i is at address: %p\n", &i);
    
    i = 2 * 2;
    printf("i = %d\n", i);
    printf("i is at address: %p\n", &i);
    return 0;
}
```

This gives us the output:
```
i = 100
i is at address: 0x7ffd582272e4
i = 4
i is at address: 0x7ffd582272e4
```
We use the `%p` flag here to print the memory address, using the pointer. Notice how though the value of 'i' changed, it's memory address remains the same.

`printf` also gives us the capability to format floats and integers, with left and right justify, rounding and exponential notation, according to our needs.
```c
#include<stdio.h>

int main()
{
    int x = 17, y = 44992;
    float m = 39.7772, n = 783530.2;
    printf("|%5d|%-7d|%10.2f|%.4f\n", x, y, m, n);
    printf("|%.3d|%8.3d|%g|%10.3e|\n", x, y, m, n);
    return 0;
}
```

The above code outputs:
```
|   17|44992  |     39.78|783530.1875
|017|   44992|39.7772| 7.835e+05|
```
Now let us carefully take note of how each flag modifies the output. First let as look at the first row printed.
`%5d` tells `printf` to print an integer and to use at least 5 characters to print it, so the function prints spaces behind the number to do this, right aligning it in the process.
`%-7d` does essentially the same thing, but it tells the function to print the spaces after the number, left aligning it.
`%10.2f` tells `printf` to use 10 characters to print a floating point number, and to only print up to 2 decimal places, note how it rounds the number to the necessary number of decimal places. 
`%.4f` allows us to print 4 decimal places of the number, even though the number doesn't have 4 decimal places. The expectation is that zeroes would be added, but due to how floating point numbers are implemented and stored in memory, the error means that when we reveal more than what we have assigned, we can often see that the number was not stored exactly as we had entered it.

Now coming to the second row printed.
`%.3d` lets us print 3 digits of the integer, prepending a 0 in this case to make it have 3 digits.
`%8.3d` prints the number so that it occupies 8 spaces and uses at least 3 digits, not a problem here since our integer is larger than that.
`%g` is an interesting flag which prints the shortest representation for the number.
`%10.3e` prints the float in exponential form, taking up 10 characters, and giving at least 3 decimal places.
