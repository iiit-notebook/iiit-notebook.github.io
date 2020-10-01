---
title: Lecture 4
code: cs0.101
number: 4
---
## Sequential execution model

In a sequential execution model, statements are executed serially. The fetch-decode-execute cycle runs on a single thread. This is contrasted by *parallel execution model* where tasks are performed on multiple threads with it not being necessary that one task must be finished before the next one starts.

## Previous standards for C

The current C standard is C18, though the language has not changed significantly since C89/C90. This standard for example does not allow the use of *C++ style comments* (`// comment`) and only allows *C style comments* (`/* comment */`).
GCC allows us to specify which standard of the language we wish to use by using the `-std` flag. 

For example, to compile a program using the C89 standard, we can enter the following command in our shell:
```bash
gcc -std=c89 file.c 
```

This allows for great *backwards-compatibility*, which makes *legacy* software easier to maintain.
