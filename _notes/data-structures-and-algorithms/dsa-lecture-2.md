---
title: DSA Lecture 2
date: 2020-02-22
number: 2 
code: cs1.201
author: Varshita Kolipaka, Anusha Nath Roy, Vidit Jain
---
Define data types:

Native Operations: `+` `.` `-` `/`

`math.h` brings about sine and cosine

When creating custom data types, we must answer 2 questions:

1. The values it can take
2. The operations you can carry out on it

---

## ADT (Abstract Data Types)

Class of objects whose logical behaviour is defined by :

1. Set of Values 

2. Set of Operations

(1. Set of Values 2. Set of Operations) - Precursor to OOP

---

### **Example :**

Creating a Complex Number abstract data type (ADT), in a file `complex.h`

When you specify a data type you also specify what values it can take. 

### 1. Data type (Set of Values):

```c
// {a + ib} ==> struct data type
typedef struct complex2_ complex2;
struct complex2_
{
	double a; // real
  double b; // imaginary
}

// way 1
struct complex2_ c1;
c1.a ==> real
c2.b ==> imaginary

//way 2 typedef
complex2 c1;
c1.a ==> real
c2.b ==> imaginary
```

`typedef`, unlike a macro, doesn't simply replace a string. 

```c
typedef struct complex2_ complex2;
	//{a+ib}
struct complex2_{
	double a; //real
	double b; //imaginary
};
```

Use of `typedef`

`typedef` in simple terms is basically just renaming terms for the code to make a bit more sense

```c
typedef int* PtrToInt;
PtrToInt x;
```

This allows us to use `PtrToInt` instead of saying `int`. We use `typedef` in `complex.h` so we can say `complex2` instead of typing out `struct complex2_` every single time

### 2. Operations which are permitted for data type:

```c
//Operations which are permitted for data type:
typedef struct complex2_ complex2;
typedef complex2 polar2; //reusing
struct complex2_{
	double a; //mag
	double b; //angle
};
// we use same and convey or represent different things

//proper ==> operations with one complex no
complex2 CxCreate (double real,double image);
double CxMod (complex2 cx); // finds mod |a+ib|
double CxArg(complex2 cx); // atan2(b,a)
complex2 CxConj(complex cx); // Returns a - ib as a complex2_ struct
polar2 Cx2Polar(comple2 cx); // 

//operations on 2 complex numbers
complex2 CxAdd(complex2 c1, complex2 c2); // Adds two complex numbers
complex2 CxMult(complex2 c1, complex2 c2); // Multiplies two complex numbers
```

We can reuse structures, if the structure is similar. Here, we make a statement `typedef complex2 polar2` because in a polar coordinate complex number data type  $re^{i\theta}$, we also need to have only two real numbers, `r` and `theta`.

This can abstract out the process behind each such operation. 

### How to implement the ADT?

In a source code file, do the following:

```c
// in complex.h

#ifndef __COMPLEX_H // if not defined before define 
#define __COMPLEX_H // protecting the header file

//All the content of the complex.h file

#endif  // end if

/*
 will ensure that these will be defined only once because 
 the next time you #include "complex .h" the macro will already be defined 
 so will not enter #ifndef because it is defined.
*/  

```

```c
// in complex.c file

#include "complex.h" // " " shows that it's user defined

```

When we use `<>` when including a header file, we tell the compiler that we are including a standard header file. If we use `""` we tell the compiler that we are including a user defined header file.

---

### Precaution

One shouldn't include function definition in the `.h` file. You're inevitably going to violate the One Definition Rule. 

After preprocessing, each source file will contain the header file. Then, at the linking stage you will end up with a multiple definition error because you will have multiple definitions of the same function.

Using `inline` or `static` will get rid of the linking error. Unless you want the function to be `inline`, it is best to *declare* the function in the header and *define* it in a single source file and link it.

---

The header file gives enough information to represent an ADT, as it shows the structure of the data type, as well as the operations that can be carried out on it.

It implements concept of abstraction.

### Difference between ADT and Data Structures:

ADT describes the WHAT (the interface)

1. *WHAT* data is stored
2. *WHAT* operations are supported

Data Structures describes the HOW (the implementation)

1. *HOW* data is stored
2. *HOW* operations are implementations

Here,

`complex.h` ⇒ ADT : As it only contains WHAT functions will be defined, and parameters

`complex.c` ⇒ Data Structures : As it actually defines the functions, and implements them

Looking at the header file should be sufficient to get an idea of the Abstract Data Type being implemented. Making use of Abstract Data Types, keeping header files separate is a good practice, as it's an abstraction and makes it easier to understand the code.

---

### Real life example of ADT vs Data Structure:

Say you try to buy an ice cream from a machine. You only worry about what you can do with the machine, and what you can get from it. This is the Abstract Data Type part of the machine

The Data Structure part of the machine is the working of the machine, and what must it execute to carry out its functions.

It is not necessary that we know how the machine works for using the machine. This is called abstraction.

---

### Arrays:

Not first class data types in C. 

A **first-class citizen** (also type, object, entity, or value) in a given programming language is an entity which supports all the operations generally available to other entities. These operations typically include being passed as an argument, returned from a function, modified, and assigned to a variable.

---

### Collections:

Process involves a collection of same data types. They can be organised by any relevant comparator. It is possible to use various program structures to represent them. 

Program Structures = Data Structures 

When one creates Collection-style data type, it's expected that they have these operations -

`create` - Create a collection

`add` - Add an element to a collection

`delete` - Delete an element from a collection

`find` - Find an item matching some criterion in the collection

`destroy` - Destroy the collection

---

### Data Structures:
**Primitive Data Structures**

1. Integer
2. Real
3. Character
4. Boolean (Exists primitively in C++, not C)

**Non - Primitive Data Structures**

1. Linear Data Structures
    1. Arrays
    2. Linked list
    3. Stacks
    4. Queues
2. Non linear data structures
    1. Trees
    2. Graphs