---
title: C Pro Lecture 23
author: Vidit Jain
code: cs0.101
number: 23
---
## Set of functions to modify numbers using bitwise operators.

### Setting a bit
```c
int setBit(int N,int pos){
    unsigned int mask= 1<<pos;
    N = N | mask;
    return N;
}
```
Say that we have a number N, and we want to set a particular bit in the number. Setting a particular bit means to flip it to 1, if it was zero earlier, or leave it as it is if it's 0.  
To set $$b_{pos}$$ to 1, we first declare a variable ```mask``` and set it equal to ```1 << pos```. Therefore, only the bit $$b_{pos}$$ will be set, while all the others will be zero.  
Say we look at the bit $$b_{i}$$ where $$i \neq pos$$. We know that in mask, the only set bit is $$b_{pos}$$ while all the others are 1, therefore, if we use the bitwise OR operator |, for the $$i^{th}$$ bit, declaring the $$i^{th}$$ bit of N as x, the boolean expression can be written as x OR 0 $$= x,$$  $$ x \in \{0,1\}$$. Hence, we know that for all bits except for $b_{pos}$, the bit value of N will remain the same.  
Taking $$b_{pos}$$, and calling the bit of N at position _pos_ as x, the boolean expression can be written as x OR 1$$= 1,$$ $$x \in \{0,1\}.$$ Therefore, the value of $$b_{pos}$$ will be 1, regardless of the value of x.

Say we take $$N = 20_{10} = (00010100)_{2}$$
And we want to set $$b_{pos}$$ where $$pos=0$$
We create mask as ```1 << 0``` which will give us ```00000001```.
Using the OR operator, we'll get
```
00010100 | 00000001 = 00010101
```
Hence setting the $$0^{th}$$ bit of 20 gives us 21.

So if you call ```setBit(20,0)```, it will set the $$0^{th}$$ bit as 1, and will return the value 21.  
If you try to set a bit that's already 1, there will be no change. Say we take $$N=20$$, and we try to change bit 2.

```mask = 1 << 2``` which will give ```00000100```

```
00010100 | 00000100 = 00010100
```
Therefore if you call ```setBit(20,2)``` it will return the value 20.


### Masking a bit

```c
int maskBit(int N,int pos){
    unsigned int mask= 1<<pos;
    mask = ~mask;
    N = N & mask;
    return N;
}
```

When we say that we want to _mask_ a certain bit, we mean that we want to flip it to 0 if it was 1 earlier, or don't change it if it was already 0.

Here we'll make use of the properties

x AND 1 $$= x$$,  $$x \in \{0,1\}$$  

x AND 0 $$= 0$$,  $$x \in \{0,1\}$$

We need to create mask such that all the bits except for pos are 1, so that the bits of N aren't changed, and the $$b_{pos}$$ is 0, so that irrespective of the value of $$b_{pos}$$ in N, the new value of the bit will be zero.  
To achieve this, we first assign a value ``` mask = 1 << pos ```. In mask, all bits except $$b_{pos}$$ are zero, while $$b_{pos}$$ is 1. We want the opposite of this, so we use the compelement operator ( ~ ) to flip all the bits i.e. make all the ones into zeros, and vice versa.

Therefore, after complementing the bits in mask, we then use the \& operator between N & mask to set $$b_{pos}$$ of N to 0.

Say we take $$ N = 21_{10} = (00010101)_{2} $$ And we want to mask $$b_{pos}$$ where pos = 0. We initialize mask as ```1 << 0 ``` which will give us ```00000001```. Then we use the complement operator to give us ```11111110```.

```
~(00000001) = 11111110
```
We then use the & operator
```
00010101 & 11111110 = 00010100
```
Hence, masking the $$0^{th}$$ bit of 21 gives us 20.

So, if you call ```maskBit(21,0)```, it will mask the $$0^{th}$$ bit as 0, and return the value 20. If you try to mask a bit that's already zero, there will be no change. Say we take $$ N = 21 $$, and we try to change bit 1.

```mask = 1 << 1``` which will give ```00000010```, and complementing it would give ```11111101```.

```
00010101 & 1111101 = 00010101
```
Therefore, if you call ```maskBit(21,1)```, it will return the value 21.

## Pointers (Coming Soon...)

