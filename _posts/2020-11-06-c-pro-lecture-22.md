---
title: C Pro Lecture 22
author: Pratyaksh Gautam
code: cs0.101
number: 22
---

[The lecture recording](https://youtu.be/gA8wD9qbDpU)
## Preprocessor macros: conditionals

We can use conditionals even in the preprocessing stage by using macro conditionals:
```c
#ifdef DEBUG
	printf("We are debugging!\n");
#endif
```

If we either at a line at at the top, `#define DEBUG 1`, or if we compile using the following command then we the `printf` statement is executed and we get the output:
```
$ gcc -DDEBUG debug.c
 We are debugging!
 ```

 The code is replaced *before* compilation by the preprocessor, so if `DEBUG` is not defined, then the code sent to the compiler from the preprocessor does not have the line containing the `printf` statement at all.
 The inclusion of that line is a **compile-time decision**.
 This can be very convenient to manage debugging of the program while still keeping it production-ready.

## Loop invariants

Loop invariants refer to a 'property' of the code which is true for every iteration, and we maintain this throughout the successive iterations. What this means is that at the beginning of every iteration of the loop, we have a certain fact we know to be true, and we can use this for the logic of the loop.
By the end of the iteration we ensure that the invariant will be true for the next iteration too, so we can use it again in the next iteration.

It is important to understand that loop invariants are not a feature of the C language, but just a concept that we use in order to keep better track of the logic of our code in a loop.

## More on assertions

We have seen assertions in the past and understand their use case. It is important to notice that assertions are **run-time decisions**.
We can use assertions in conjunction with the concept of our loop invariants too, checking that the loop invariant is true at the beginning of every loop.
Since the assertion fails and aborts the program telling us where we went wrong if our invariant is not valid, it can be very helpful in debugging.

*Note: If we wish, we can also disable assertions by defining the macro `NDEBUG`.*

## Bitwise operators

At the hardware level, the smallest data size that we can read and write is 1 byte (8 bits).
However there are also operations that we can and may want to conduct on individual bits, which are known as bitwise operations.
These include bitwise `AND`, `OR`, `XOR`, etc. Their effects can be represented using familiar truth tables.

```
10000100 AND 01000110		= 00000100
10000100 OR  01000110		= 11000110
10000100 XOR 01000110 		= 11000010
```
In C, and many other programming languages, the symbols to perform the 'AND', 'OR' and 'XOR' operations are ``` & | ^ ``` respectively.  
Say that you want to use these operations on the numbers 150 and 163.  

First, we convert these numbers into binary

$$150_{10} = (10010110)_{2}$$

$$163_{10} = (10100011)_{2}$$

Then we apply the bitwise operators.
```
10010110 & 10100011 = 10000010
10010110 | 10100011 = 10110111
10010110 ^ 10100011 = 00110101
```
Therefore, the operators will give the numbers 130,183 and 53 respectively.  

```c
#include<stdio.h>
int main(){
	int a = 150, b = 163;
	int logicalAND = a & b;
	int logicalOR = a | b;
	int logicalXOR = a ^ b;

	printf("a & b = %d\n",logicalAND);
	printf("a | b = %d\n",logicalOR);
	printf("a ^ b = %d\n",logicalXOR);
}
```
Will give the output
```
a & b = 130
a | b = 183
a ^ b = 53
```
### Bitwise shifts
We can also shift the bits to the left or the right. Consider the left shift `<<` in the following situation
```
[ b7 b6 b5 b4 b3 b2 b1 b0 ]
<<	//shift by one
[ b6 b5 b4 b3 b2 b1 b0  0 ]	// b7 "falls off"

[ b7 b6 b5 b4 b3 b2 b1 b0 ]
>>	//shift by one
[  0 b7 b6 b5 b4 b3 b2 b1 ]	// b7 "falls off"
```

The above logic is perfectly valid for unsigned integers, but because of the way that we represent signed integers means that it isn't so clear cut for signed integers.

## A set of function to print the bit representation of a number

### Reading Bits
```c
void readBit(int N, int pos)
{
	unsigned int mask;
	mask = 1 << pos;
	return (N & mask)? 1: 0;
}
```
The above functions takes a number `N` and returns its `pos`'th bit.
Note that `mask = 1 << pos` gives a bitstring such that all its bits are `0` except the bit at the `pos`'th position.
So when we do an `AND` operation against `mask`, all but the `pos`'th bit will definitely output a `0`, and the `pos`'th bit of N will output whatever its own value is.  
Thus, we just use the ternary operator to return `0` if that bit is `0`, and `1` otherwise. 

Say that you have a number 154  


$$154_{10} = (10011010)_{2} $$

We want to check if the 4th bit from the right is 0 or 1.
therefore we'd call the function as ```readBit(154,4)```

In the function _readBit_, the variable mask will be assigned a value ```1<<pos```  which is basically $$2^{pos}$$, so mask will be equal to $$2^{4} = 16_{10} = (00001000)_{2}$$

In the return line, we check the value of ``` N & mask ```


```
10011010 & 00001000 = 00001000
```
Therefore the resultant is 16, which is non-zero. Hence, the bit as pos=4 is set (equal to 1), So we return 1, else we return 0.
### Printing Bits
```c
void printBits(int N)
{
	printf("(%d)_2 : ", N);
	for (int i = 8 * sizeof(int); i >= 0; --i) {
		printf("%d", readBit(N, i);
	}
	printf("\n");
}
```
Now this function just calls the above function, and prints the relevant bits in order.
