---
title: C Pro Lecture 30
author: Pratyaksh Gautam
code: cs0.101
number: 30
---

## Continuing the improved program

### the `main` function

```c
int main(void)
{
    char **names;
    int nonames;    // scalar variable of type integer

    nonames = readNames(&names);
    printNames(names, nonames);
    sortNames(names, nonames);
    printf("Sorted Name List\n");
    printNames(names, nonames);

    return 0;
}
```

Our `main` function contains a variable `names` which is a pointer to a set of char pointers, which we use to store strings.
We will reference the `readNames` call in the next section.

### the `readNames` function

Our `readNames` function now takes in a "third degree pointer", a pointer to a pointer to a char pointer. What this means is that `pnames` contains the address of a pointer, and that pointer points to the base address of a string, with other strings adjecent to it, (and we know strings are just `char *` with null terminators).
It's return type is `int`, it returns the number of elements in the list.
```c
int readNames(char ***pnames) /* pnames contains a pointer to names (from main) */
{
    char current_name[MAX_NAME_LENGTH];
    char **names;
    int i = 0, length, curr_max_size = INIT_LIST;

    names = (char **) malloc(INIT_LIST * sizeof(char *)); /* We ask for space to hold the pointers */
    *pnames = names; /* now our original names (from main) points to that newly allocated memory*/

    while (scanf("%s", current_name) == 1)
    {   /* for each name in our list */
        length = strlen(current_name); /* we get its length */
        names[i] = (char *) malloc(length+1); /* allocate the neccessary space for it (including null terminator) */
        strcpy(names[i], current_name); /* and copy it into the array */
        i = i + 1; /* increment our counter */

        /* wash, rinse, repeat */
        if (i == curr_max_size) { /* If we run out of space this way */
            curr_max_size += SIZE_INCREMENT; /* increase the size of our list */
            names = (char **) realloc(names, curr_max_size); /* and just reallocate the memory, so we can keep going! */
        }
    }

    return i;
}
```

`realloc` function allows us to take a pointer which he had previously allocated some memory in the heap, and now make it point to a seperate block of memory in the heap of our desired size.

We called `readNames` in the below line in `main`. We did this because we need to modify `names`, so we must pass a **pointer** to `names`, which we are storing in the function itself as `pnames`

```c
    nonames = readNames(&names);
```
