---
date: 2020-12-04
title: C Pro Lecture 34
author: Pratyaksh Gautam
code: cs1.101
number: 34
---

## Structures
A structure is a collection of values, which do not necessarily need to have the same type.
We can declare a structure in the following way:
```c
struct {
	int id;
	char category;
} vol1, vol2;
```

The above code declares two structure variables, `vol1` and `vol2`, each of which is made up of two variables, `id` and `category`.  
We can access these members using the `.` operator.
```c
vol1.id = 10;
vol2.category = 'c';
printf("id of vol1 is %d\n", vol1.id);
printf("category of vol2 is %c\n", vol2.category);
```

The structure is stored as a continuous block in memory. Variables declared *within* the structure declaration are limited to that scope, so they won't conflict with variable names elsewhere in the program.  
We can name a structure if we want to use it for various variable declarations throughout the program.
```c
struct book {
	int code;
	char category;
	char name[MAX_LENGTH + 1];	// MAX_LENGTH must be a defined macro
}
```
Now we can declare structures further ahead in the program like so:
```c
struct book book1;
```

The C language syntax requires us to use the `struct` keyword. It is a fairly common practice to `typedef` it into a new data type so that we do not have to repeatedly use the `struct` keyword.

```c
typedef struct book Book;	// define the data type 'Book'
Book book2;			// now this declaration is valid for 'book2'
```

Consider the following program and its output, which will further clarify how we can manipulate data stored in structures.
```c
#include<stdio.h>

typedef struct book {
	int id;
	char category;
} Book;

main() {
	Book tesla, hooke;
	tesla.id = 10; tesla.category = 'a';
	Book einstein = {9, 'a'};
	Book newton = {.category = 'a', .id = 8};
	hooke = newton;			// valid; copies values of newton to hooke
}
```

Structures can be copied as shown, all the corresponding elements get copied from one struct variable to the other (including any arrays).  
Structures can also be put in arrays, like so:
```c
Book library[10];
library[1].code = 10;			// how we access elements in the array
```

## Unions
Unions are a way of storing date of various different types together in the same address.
To better illustrate the idea, see the declaration of a union below:
```c
union {
	char c;
	int i;
	double d;
} u;
```
It is important to note the difference between unions and structures. Unions do not allocate separate space for each member type, just the largest one.
The union `u` is assigned the space needed for the largest member in it, in this case the double `d`.
It has multiple applications, a very important one of which is to save space.
We can declare unions in this way so that we know we will be able to safely store any one of the member types in it.

The same memory is thus made available to be used and interpreted as different data types.

As an example to illustrate the use of unions better, consider:
```c
u.c = 'a';
printf("%c\n", u.c);
u.i = 10;
printf("%d\n", u.i);
u.d = 9.99997;
printf("%lf\n", u.d);
```
`u.c` interprets the value in `u` as a `char`, `u.i` interprets it as an `int`, and `u.d` interprets it as a double.

## Enumerations
Enumerations are very useful data types, best illustrated by a simple example:
```c
/* Simple program to print the day name given day number (in week) */
#include<stdio.h>

int main()
{
	enum {mon, tue, wed, thu, fri, sat, sun} day;
	char input[100];
	printf("Enter the day number: ");
	scanf("%d", &day);
	switch(day - 1) {	// convert indexing from 1 to indexing from 0 (enums index from 0)
		case mon:	printf("Monday\n");	break;
		case tue:	printf("Tuesday\n");	break;
		case wed:	printf("Wednesday\n");	break;
		case thu:	printf("Thursday\n");	break;
		case fri:	printf("Friday\n");	break;
		case sat:	printf("Saturday\n");	break;
		case sun:	printf("Sunday\n");	break;
	}
	return 0;
}
```

Thus the use of `enum`s (enumerations) here helps improve the readability of the program greatly and eliminates confusion about what the possible values of `day` might represent.
