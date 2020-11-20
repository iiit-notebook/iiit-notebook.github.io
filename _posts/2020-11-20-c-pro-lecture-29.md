---
title: C Pro Lecture 29
author: Pratyaksh Gautam
code: cs0.101
number: 29
---

## Writing a *better* program to sort a list of names

The last program we wrote to sort a list of names has a few shortcomings:
- Names can't have spaces.
- Limited length of name (20 characters)
- Lots of space is wasted in the 2D arrays

Now, we'll write a **dynamic memory allocation** based program in order to overcome these issues.

```c
char names[MAX_LIST][MAX_NAME_LENGTH];  // what we had earlier
char *names[MAX_LIST];                  // what we will use now
```

Since `*names` is an array of `char` pointers, each name can have a different size, meaning it is more memory efficient.  
Now, we have to change `readNames()` accordingly:
```c
inr readNames(char *names[])
{
    char current_name[MAX_NAME_LENGTH];

    int i = 0;
    while ( scanf("%s", current_name) == 1) {
        length = strlen(current_name);
        names[i] = (char *) malloc(length); // malloc() is called to allocate memory
        i = i + 1;
        if (i == MAX_LIST)
            break;
    }
}
```

`malloc()` allows us to allocate a given amount of memory to our program from the heap, and it returns a pointer to it.
The memory which is allocated through `malloc()` is **not** released once we reach the end of the function.
This function is present in the headerfile `malloc.h`.
We have to explicitly free it using a function known as `free()`.

Thus, we have complete control over how we use the memory in the heap this way, when we allocate it and when we free it.

## Understanding pointer arrays

```c
int var;        // A single integer
int *var;       // A pointer to an integer
int *var[10];   // An array of pointers
```

It is important to have a clear understanding of what each of these variables represent.  

The first one, `int var`, is quite trivial, it is simply an integer.  
The second one, `int *var`, is a *pointer* to an integer.
It holds the address for a single integer variable.  
We can use the pointer not only to refer to the memory address of that variable itself, but also other memory addresses relative to it.  
This is what allows us to use a single pointer to access any element in an array, since arrays are stored in contiguous (adjacent) memory addresses.  
The last one, `int *var[10]`, is an *array of pointers*.
This means that each element of `var` holds an pointer, pointing to the memory address of some integer.  
We can make these pointers point to different memory addresses, including the base addresses of some other integer array.  
In this way, we can access multiple integer arrays, and keep them neatly stored together using pointers, and there is no limitation on the individual arrays.  
They need not all be arrays of the same size, which allows for better space efficiency than 2D arrays.

This is especially common in case of strings i.e. null-terminated character arrays.
```c
char *names[10];
```
This refers to an *array of pointers* to characters. We have already seen that strings can be referred to by the base address of their first element, similar to other arrays.  
That means that in this array, we can effectively store multiple strings of different sizes, and since it is an array of pointers, we can use these pointers to point to each of these strings.
