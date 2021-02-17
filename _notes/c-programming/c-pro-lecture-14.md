---
date: 2020-10-14
name: C Pro Lecture 14
author: Pratyaksh Gautam
code: cs0.101
number: 14
---

[The lecture recording](https://youtu.be/DXfBUg45cdE)
## Arrays

Up till now, most of the variables that we used were standalone *scalar* variables.
There is also a convenient feature of C, known as **arrays**.
Collections of variables can be stored together in these arrays

```c
int A[10];
```
This declares an integer array of size 10, i.e. 10 integers can be stored together in this array. Arrays store data in *contiguous memory*, which means that if A[0], the first element is stored at address `0x40`, then the next element A[1] would be stored at `0x44`, since size of int is 4 bytes, and so on.

The memory addresses are not fixed. The initial address of the array may change between executions, but the memory addresses of subsequent elements remain continuous.

```c
int main()
{
	int n[10] = {1, 0, 7};
	for (int i = 0; i < 10; i++)
		printf("%d ", n[i]);
}
```
As seen above, we can initialize elements of the array this way too, instead of manually entering each element separately. This produces the output
```
1 0 7 0 0 0 0 0 0 0
```

An uninitialized array will have garbage values filled in it, but if we initialize it with the above method, the specified elements get assigned the respective values,
and the remaining elements are assigned '0' by default. In fact this is a quick and dirty way to initialize an array to all zeroes.
```c
int n[10] = {};		//Initializes the array to 10 zeroes
```
