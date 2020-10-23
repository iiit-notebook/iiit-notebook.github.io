---
title: C Pro Lecture 18
author: Vidit Jain
code: cs0.101
number: 18
---
## Functions _continued_
We'll take an example of a C program that has 3 functions:
* The main function 
* A function that returns the average of two integers
* A function that returns the max of two integers 

```c
#include <stdio.h>
int max(int a,int b){
    if(a>b)
        return a;
    else
        return b;
}
float average(int a,int b){
    float result=(a+b)/2.0; 
    /*We divide by 2.0 so a float is returned so 
    that the fractional value will not be truncated*/
    return result;
}
main(){
    int A,B;
    printf("Enter numbers A and B: ");
    scanf("%d %d",&A,&B);

    printf("The average of A and B is: %f",average(A,B));
    printf("The max of A and B is: %d",max(A,B));
}
```  
In this program, we define a function max, that takes two integers, compares their values and returns the value that is greater. By defining this function, in the main function we can basically find the max of two integers by using max(A,b).  
Similarly we define a function average, a function that takes two integers and returns a float, the average of the two. (Note that we divide the sum of a and b by 2.0 and not 2, since we want the fractional part of the average.)

## Uses of functions
### Modularity
If instead of keeping all the code inside one main function, we divide the code into multiple functions, it becomes much easier to debug programs and makes code more readable.

By making use of functions, you are basically taking one problem, and splitting it into multiple subproblems that can be solved and coded separately. This can be of great use when a group of people are working on a project. The responsibility can be split more easily, with each member assigned a task of solving a specific subproblem rather than all of them working on 1 main function.

### Code Reusability
It's quite common for a programmer to use a block of code multiple times in a program. Say that in a code, you are required to sort an array multiple times, at various places. Instead of writing the sorting algorithm multiple times whenever you need an array to be sorted, a sort function can be created instead, that would take an array as a parameter and sort the function. Therefore, sorting the array would be reduced to basically making a simple function call.

## Bitwise operators
There are multiple bitwise operators in C, but for now we'll focus to the bitwise shifting operator,  
<pre>
<<  
</pre>

Say we take the number 1, which in binary is 00000001
```c
int x = 1 << 3
```
In this command, 1<<3 is basically telling us to shift the bits of 1 left, 3 times.  
```
00000001
00000010
00000100
```
We know 00000100 is 8 in binary, therefore ```1<<3``` will basically return 8, hence x=8  
Note, we can make use of ```<<``` for numbers other than 1. Take the number 13 (00001101) and shift it 4 times.
```
00001101  
00011010  
00110100  
01101000  
11010000  
```
11010000 in decimal is 208. If you notice, each bit shift to the left is basically multiplying the number by two. Therefore, ```1<<3``` can be written as $1 \times 2^{3} = 8 $, and ```13<<4``` can be written as $13 \times 2^{4} = 208$

Therefore ```a<<b``` in mathematical terms can be written as $a \times 2^{b}$

**NOTE** Using the ```<<``` operator can lead to somewhat of an _overflow_  

Say we take an 8 bit integer, 11010000 and shift it once to the left

```
11010000
10100000
```

Therefore, if in an integer, the leftmost bit is one, and the numbeer is shifted once to the right, the 1 will be _dropped_.
## Scope and Lifetime of Variables
If we look at the function average, the variables declared inside it: a,b and result are restricted to be used in average itself. Therefore, if a different function, say a main function tries to directly access the a,b or result variables of average, an error will be thrown by the compiler saying that the variable is undefined.

Therefore, the scope of the variable result is limited to the average function. The moment the function is invoked, the result variable is declared, and once the function call is finished, the memory occupied by the variable result is freed.


## Pseudo-Random Number Generator

```c
#include <stdio.h>
#include <time.h>
#define a 1103515245
#define c 12345
#define m (1<<31)
unsigned int X; 
etc in the file.
void my_srand(unsigned int seed){
    X=seed;
}
unsigned int my_rand(){
    X = (a*X+c)%m;
    return X;
}
int main(){

    my_srand(time(0));
    printf("Random number %u\n",my_rand());
}

```
Here we create a pseudo-random number generator.

In this code, a global variable X is declared. Since it has **global scope** it can be accessed by all the functions in the class, including the main function.

The execution starts from the main function. 

We call the my_srand function, passing time(0). What this basically does is assign the X variable a _seed_, the current system time.

In the next line, when we call the my_rand() function, the function performs the assignment  
 $X = (a \times X + c)\mod m$  
to create a "**_random_**" number, and returns the new value of X, which is  printed using the printf statement.
 
## Masking of variable and function names

 ```c
float average(int a,int b){
    float average=(a+b)/2.0; 
    
    average(2,3); // This will give an error 
    
    return average;
}
```
In the above function, we've declared a variable, with the same name as the function it's in. However, in C, this is allowed, and the token **average** will be redefined as a variable. Therefore, calculations and assignments can be made to average since it now identifies a variable. However, if we try calling the function average, after declaring a variable of that name, the compiler will give an error, saying that the function average is _undefined_. Therefore, the declaration of the variable average has **_masked_** the function definition of average.

If we comment out the average function call within the function, there will be no error.
```c
float average(int a,int b){
    float average=(a+b)/2.0; 
    
//    average(2,3);
    
    return average;
}
```
If we want to access the average function instead, we can comment out the average variable declaration
```c
float average(int a,int b){
    //float average=(a+b)/2.0; 
    
    average(2,3);
    
    return 1.0;
}
```
Note that we cannot return average, since average is a function and not a variable, therefore we just returned an arbitrary float value.