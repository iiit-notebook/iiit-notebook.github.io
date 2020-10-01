---
title: C Pro Lecture 7
code: cs0.101
number: 7
---
## Layout of a C program

- Every C program is a collection of .c and .h files.
- Each file is a collection of functions.
- Every function is a collection of statements.
- Every statement is a series of tokens.

Tokens are (bla bla). The amount of space between tokens usually is not important, as long as they do not get merged together. The compiler ignores excess whitespace.
However putting a newline character in a string literal is illegal
```c
printf("To C, or not to C:
that is the question.\n");
/***WRONG***/
```

## ASCII and characters

Look at the below code:
```c
#include<stdio.h>
int main()
{
    char letter = 'A';
    printf("%c -- %d", letter, letter);	    //Output: A -- 65
    return 0;
}
```
So here, the `%c` placeholder prints the character, and the `%d` placeholder prints the ASCII value of the character. This is because in memory, 'A' is encoded as 65 (in binary). The place holder just changes the *way* those bytes are interpreted, as an ASCII code for a character, or as an integer itself.
Now, obviously it can be troublesome if A is output as 65 in a program where it wasn't expected. This is why we must take care of our data types. It is the data type for a variable which tells the compiler how to read that binary encoding in the memory.
We can get some unexpected behaviour from our program if we try to read a float in binary encoding as a decimal, for eg., because these data types are encoded differently.
C does allow for *typecasting* to convert between different types, but there are rules for that which we will discuss later.

## Escape characters

Often times we want to print special characters such as double quotes, percent symbols etc. in a string literal, without the C compiler considering it as an individual token, but a part of the string.
To do this, we have to use escape sequences in the string. We are already familiar with `\n` to signify a newline character, but we also have `\t` for tab, `\"` to print literal double quotes, `\\` to print backslash and so on. If we want to print a percent symbol, we use `%%`. 
We can even escape literal newlines in our string literals by adding a backslash before pressing `<Enter>`. This can improve readability for very long strings.
```c
printf("Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras ac augue vitae velit lacinia pellentesque non eleifend\
	 odio. Fusce feugiat scelerisque dolor, vitae maximus enim sodales sit amet. Nulla non auctor velit. Nunc a \
	dictum felis.");
	/***LEGAL***/
```
Now we don't have to type `printf` multiple times!

## scanf and its sensitivity to data types

(need to review and experiment some with scanf)
(keyboard buffers and scanf failure?)
