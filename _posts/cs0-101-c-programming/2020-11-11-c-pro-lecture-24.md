---
title: C Pro Lecture 24
author: Pratyaksh Gautam
code: cs0.101
number: 24
---

## Swapping two numbers

A simple problem to solve, if we have `a1` and `a2` we can swap their values using a temporary variable `temp`.
```c
temp = n1;
n1 = n2;
n2 = temp;
```

While swapping like this is simple, it is very fundamental to many algorithms, especially sorting algorithms, so we might want to abstract it into a function like this:
```c
void swap(int A, int B)
{
	int temp;
	temp = A;
	A = B;
	B = temp;
}
```

There is however a small problem with the above code: **it doesn't work.**  
`A`, `B`, and `temp` are local variables, so as soon as we leave the function scope their lifetime is over.
The actual values of the variables we pass to the function are unaltered.

To fix this, we need to pass the addresses instead of the variables, and we do this with the help of **pointers**
```c
void swap(int *A, int *B)
{
	int temp;
	temp = *A;
	*A = *B;
	*B = temp;
}
```

Now this function will work because we have used pointers to directly access the memory locations.
We are directly changing the variables right where they are stored, in a sense, instead of working on a copy of the variables.

## Call-by-Value

It is important to note that C follows a 'Call-by-Value' mechanism; that is to say that it only copies the value of the parameters given to a function to be used in the local scope.  
Since we only have the values of the variables, we are in a sense working on copies of the variables given as parameters to the function.

*So how then did we implement that swapping program, if we can only get values copied into the function?* This is what we used **pointers** and **memory addresses** for.

First note that when we call the above function we have to do so like this:
```c
int n1 = 3, n2 = 7;
swap(&n1, &n2); 	// now, n1 = 7, n2 = 3
```

The ampersand (`&`) is used to give the *memory address where n1 and n2 are stored* instead of the value of n1 and n2.  
So this means that the function received memory addresses, which is why we had `int*` variables as our paramaters.
We actually initialized these local integer pointer variables with these addresses.

So now we have pointers in our local function scope, which point to memory locations for variables in the scope of the main function.  
This is what gives us the power to modify variables outside of its scope.
We can then use the `temp = *A` syntax to make changes to the variables stored at those memory addressess (which are the original variables `n1` and `n2` )

This is how we are able to implement our swap function.

## Arrays, Pointers and Pointer Arithmetic

If we declare an array, say `int A[10]`, then we can actually use the name of the array as a pointer to the base address.
```c
int A[10] = {0};
printf("&A[0] = %p, A = %p", &A[0], A);	// prints the same memory address for both
```

And if we want we can access the element at index 1 in two equivalent ways:
```c
printf("%d\n", *(A + 1));
printf("%d\n", A[1]);
```

They both print the exact same element, and the use of such operations on pointers is commonly known as **pointer arithmetic.**
