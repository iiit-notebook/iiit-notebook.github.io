---
title: Lecture 5
code: cs0.101
number: 5
---
## printf and scanf

The standard C libraries have a few very useful functions, such as `printf` and `scanf` present in the headerfile `stdio.h`. We can use them to print to `stdout`, the standard output, and read from `stdin` the standard input.

```C
int n = 4;
printf("There are %d sheep\n", n);
```
In the above line, `printf` takes two arguments, a string literal, and an integer variable. In the string literal, `%d` is a special placeholder that tells the function that we want it to print the integer variable that we 
have passed along to the function as the next argument over there. We also have an escape sequence `\n`, which tells the function to print the newline character i.e. move to the next line.

```C
int n;
scanf("%d", &n);
```
In this line of code, `scanf` takes two arguments, a string literal, and an *address* for an integer variable. The `%d` as the string literal tells `scanf` to anticipate an integer being input. The `&` is used to get the address of the integer variable, and then `scanf` writes the entered variable to the
given address.

## Macros

A macro is basically a piece of code which has been turned into a shortcut and given a name. Whenever that name is used, it gets replaced by the code we have decided for that macro. There are different types, but we'll keep it simple here.

```C
#define PI 3.14
...
    radius = 7;
    printf("The perimeter is %d\n", 2*PI*radius);
...
```
In the above code snippet, we use a macro to substitute PI with 3.14. The immediate thought is *'but why?'*, and there are a few reasons why this is a good practice:
- It improves the readability of the program.
- This allow us to change the value of it easily, which can be very important if for example we have used this value multiple times through our program and we get to know there is a more precise value we can use.
- Since macros are handled by the preprocessor, that means that the macro is replaced **before** compilation, and thus takes up no memory, as opposed to declaring a `const float`. 

## More library functions: <math.h>

`<math.h>` is a great library which contains common mathematical functions, including `floor` and `ceil` function which allow us to round floating point numbers down and up respectively, into integers. To compile a program containing a function defined in `<math.h>`, first we must tell the preprocessor to include it and we must also tell the compiler to link it by using the `-lm` flag.
`gcc mathy_code.c -o mathy_code.out -lm` allows us to compile our code properly.
