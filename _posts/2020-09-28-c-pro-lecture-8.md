---
title: C Pro Lecture 8
author: Pratyaksh Gautam
code: cs0.101
number: 8
---
[The lecture recording](https://youtu.be/Qzyh5ycGEwY)
## Number Systems

Computers completely encode data in binary, i.e. base 2. For e.g. the character 'A' has the ASCII value of 65, which is stored as (01000001)~2~.
This is because:
$$65 = 6 \times 10^1 + 5 \times 10^0 = 1 \times 2^7 + 1\times 2^0 $$
Binary numbers are not very human readable, since we normally deal with the decimal number system, or base 10. Converting between the two is not a trivial task though.

A compromise is achieved by using hexadecimal numbers i.e base 16. The *digits* 10 to 15 are represented by the characters A to F.
Converting from binary to hexadecimal is trivial; we simply break a byte down to two *nibbles* (4 bits) and then convert each individual nibble to hexadecimal, then the individual digits make up the number in hexadecimal system.
To illustrate this better,  
(01001001)~2~ after = (0100 1001)~2~ = (4 9)~16~ = (49)~16~  
It is also often notated as 0x49 or 49H.

## `rand()` function and pseudo-randomness

`rand()` is a pseudo-random generator which depends on the seed value, (given by `srand()`). While it's not capable of "true" randomness, we can get pretty unpredictable values if we seed it with the current *time*, since we can't really know exactly when the program will be run.

(insert basic example of `rand()` here)
```c
#include<stdio.h>

#define seed 2000
#define a 10
#define c 200
#define m 300

main()
{
    unsigned int X;
    X = seed;
    X = (a * X + c) % m;
    printf("%u\n", X);
}
```

This is known as a **linear congruential generator**. It is a type of pseudo random generator. It becomes clear that given the same initial conditions, the function always gives the same "random" sequence, which is why it is known as pseudo-random.

```c
#include<stdio.h>
#include<time.h>

#define a 1103515245
#define c 12345
#define m (1 << 31)

main()
{
    unsigned int X;
    X = time(0);
    X = (a * X + c) % m;
    printf("%u\n", X);
}
```

This code greatly improves our design of the random number generator since it is seeded by time, giving it a different seed every second instead of the same constant seed.
Keep in mind that the numbers are still pseudo random, but since they are seeded by time it is much more difficult to predict the numbers.

## A quadratic solver

(code one here)

Remember precedence between division and multiplication is taken from left to right.
