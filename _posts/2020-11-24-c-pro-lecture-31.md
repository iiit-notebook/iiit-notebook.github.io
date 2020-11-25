---
title: C Pro Lecture 31
author: Pratyaksh Gautam
code: cs0.101
number: 31
---

### `stdin`, `stdout`, and `stderr`

These are file descriptors, numbered as 0, 1, 2 respectively in linux. What we notmally think of as terminal input and output are `stdin` and `stdout` respectively.

## Files and file pointers

In C, we represent files as pointers to memory, `FILE *`. We have two functions very similar to `printf` and `scanf`, which are `frpintf` and `fscanf` respectively.

This allows us to read names from a file without the need for shell input/output redirection.
```c
    char line[100];
    FILE* fpointer = fopen("/path/to/input/file", 'r');  /* open the file in read mode */

```

## Commandline arguments
