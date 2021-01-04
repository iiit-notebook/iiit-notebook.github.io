---
title: C Pro Lecture 25
author: Pratyaksh Gautam
code: cs0.101
number: 25
---

## More on arrays and pointers

```c
void init_array(int A[], int array_size)
{
	for (int i = 0; i < array_size; ++i)
		A[i] = i*i;
}

void unsafe_init_array(int A[])
{
	for (int i = 0; i < 100; ++i)
		A[i] = i*i;
}
```
Given above are two functions to initialise the array. The second on is unsafe, because we hardcoded the size of the array to be `100`.
We will run into some problems if we give the function an array of size smaller than that as a parameter.

For example, if we pass it an array of size `10` (with a function to print the array as well), we get the following output:
```
A[98] = 9604
A[99] = 9801
*** stack smashing detected ***: terminated
Aborted (core dumped)
```

## Multidimensional Arrays

```c
void init_2Darray(int A[][10], int norows, int nocols)
{
	for (int i = 0; i < norows; ++i) {
		for (int j = 0; j < nocols; ++j)
			A[i][j] = i + j;			
	}
}
```

(talk a bit about above code and limitation)

```c
void init_2Darray(int norows, int nocols, int A[norows][nocols])
...
```

(the above code now works in C99, variable size 2d array)
