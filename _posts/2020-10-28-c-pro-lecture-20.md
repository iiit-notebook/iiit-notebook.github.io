---
title: C Pro Lecture 20
author: Pratyaksh Gautam
code: cs0.101
number: 20
---

## The Stack

A **stack** is an important kind of data structure in computer science.
It is a LIFO (Last In First Out) kind of data structure, which means that the last element
that we place in the stack is the first element that is removed from the stack.

Think of the stack as a stack of plates, without disturbing the balance of the stack we can place plates on the top, and take plates off the top.
These actions are called *pushing* and *popping* elements respectively.

### The Call Stack and Recursion

When we call a function, it is pushed onto the top of the call stack with its parameters as an **activation record**.
When the function executes its code and returns, its activation record is popped off of the stack.

Notice that this means that the function that was called most recently is evaluated first.
This is a fact that we exploit in a process known as **recursion**.

```c
int fact(int n)
{
	if (n == 0)
		return 1;
	else
		return n * fact(n-1);
}
```
Consider the above code, which given an integer `n` returns the factorial of `n`.
Suppose we call this function in `main` as such
```c
printf("%d\n", fact(4));
```

Now the `printf` function is ready to print an integer, which will be whatever value `fact(4)` returns.

So first, `fact()` is called with `n = 4`, so it goes to the `else` condition.
There, the function wants to return `n * fact(n-1)`, but to do this, `fact(n-1)` has to be evaluated first.
So now `fact()` is called again, now with `n = 3`, again it goes to the `else` condition.
Now again before it can return anything, `fact(2)` must be evaluated.  
This goes on till finally we call `fact(0)`, which returns `1`.
At this point, we finally can return the value for `fact(1)`, which is `1 * fact(0)` or `1 * 1` or `1`.
Then we can return the value for fact(2), which is `2 * fact(1)` or `2 * 1` or `2`, and so on till finally, we have
`fact(4)` which is `4 * fact(3)` or `4 * 6` or `24`.

```

|  fact(0)   |      |     1      |      |            |      |            |      |            |      |            | 
+------------+      +------------+      +------------+      +------------+      +------------+      +------------+
|  fact(1)   |      |  1*fact(0) |      |     1      |      |            |      |            |      |            | 
+------------+      +------------+      +------------+      +------------+      +------------+      +------------+
|  fact(2)   |      |  2*fact(1) |      |  2*fact(1) |      |     2      |      |            |      |            | 
+------------+      +------------+      +------------+      +------------+      +------------+      +------------+
|  fact(3)   |      |  3*fact(2) |      |  3*fact(2) |      |  3*fact(2) |      |     6      |      |            | 
+------------+      +------------+      +------------+      +------------+      +------------+      +------------+
|  fact(4)   |      |  4*fact(3) |      |  4*fact(3) |      |  4*fact(3) |      |  4*fact(3) |      |     24     | 
+------------+      +------------+      +------------+      +------------+      +------------+      +------------+

```

Such a **recursive** approach will take up linear space, as opposed to loops which could be used to evaluate the factorial in constant space.  
However in certain situations a recursive approach is very helpful and can make problem solving much easier.
A classic example is the [Tower of Hanoi](https://www.youtube.com/watch?v=8lhxIOAfDss).

## `static` variable

```c
int count()
{
	static int counter = 0;
	counter++;
	return counter;
}
```

The `static` keyword here is very interesting, since it tells the compiler that
we want the value of counter to be retained across multiple function calls.
This means that if we cal `count()` twice, it will give values `1` and `2`.

Note that scope is enforced by the compiler, which limits the scope of `counter` to the scope of the function `count()`.
The variable itself is stored in the data section of the program's memory, and it's lifetime is the whole program execution.
