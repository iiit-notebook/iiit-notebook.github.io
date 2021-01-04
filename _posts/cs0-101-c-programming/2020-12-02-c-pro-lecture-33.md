---
title: C Pro Lecture 33 
author: Pratyaksh Gautam
code: cs1.101
number: 33
---

## Makefiles and Make
When working with large projects, 'Makefiles' are convenient. They allow us to store general commands to compile our program in specific ways, so we can easily do that with a `make` command. It allows for variables and different 'targets'.  
Consider the following:

```make
# Makefile for executable adjust

# Parameters to control Makefile operation
CC = gcc
CFLAGS = -pedantic -Wall -g

# Entries to bring the executable up to date

mysort: main.o helper.o
	$(CC) $(CFLAGS) -o mysort main.o helper.o
main.o: main.c header.h
	$(CC) $(CFLAGS) -c main.c
helper.o: helper.c header.h
	$(CC) $(CFLAGS) -c helper.c
clean:
	rm *.o;
```

The above Makefile is just a way for us to run the commands we usually run, the compilation, but it makes certain things even easier.
The line `mysort: main.o helper.o` tells us that when the target is 'mysort', then execute the lines following it till the next target or end of file, but only if 'mysort' has not been compiled after changes were made.

To understand this better, `main.o` and `helper.o` are dependencies for `mysort`. So `mysort` target is made when these dependencies are "newer" than the target to make.  

