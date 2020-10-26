---
title: C Pro Lecture 16
author: Pratyaksh Gautam
code: cs0.101
number: 16
---

## Complexity and 'work done'

Processors work at a near constant rate of elementary instructions executed per second. So the time taken by a program to execute is effectively proportional
to the *number of elementary instructions needed to execute the program*.  
Suppose that a program can be subdivided into 3 parts, having $k_{1}$, $k_{2}$ and $k_{3}$ instructions respectively. 
Now further, let's say that the second subpart of the problem runs as a loop, it runs on input of size `N`, then this entails that the total time taken by the program to execute should be proportional to $k_{1} + N \times k_{2} + k_{3}$.

When we discuss the "time complexity" of the program, we are talking not about the exact runtime of the program (which is dependent also on the processor speeds),
but **how the program execution time scales with its input data**. We make what is known as a *constant factor approximation*, and ignore all the constant terms, terms independent of `N` and only care about the *fastest growing* part of the program.
This is what best tells us how the program scales with its input data.

Suppose the *time complexity* of a program is best defined by 
$$ T(n) = k_{1} N^2 + k_{2} N + k_{3} $$
Then we can take the constant factor approximation by simply caring about only the most dominant term in the equation as the data scales, the quadratic term in this case.
We can also remove the constant attached to it for our purposes, giving us the time complexity of $N^2$.

Taking an example of a program
```c
#include <stdio.h>
int main(){
    int N;
    printf("Enter the value of N:");
    scanf("%d",&N);
    int arr[N][N];
    for(int i=0;i<N;i++){
        for(int j=0;j<N;j++){
            arr[i][j]=i*N+j;
        }
    }
    return 0;
}
```
Here, we can see that the execution of the program depends upon the variable N. As the value of N gets greater, the execution time will increase too. We can see a nested loop (a loop inside a loop), and we can observe that the line ```arr[i][j]=i*N+j;``` will be run N*N times. There are other statements that'll also be executed, like the printf and scanf statement in the beginning of the program. We can assume the time taken by printf and scanf as just _2_, since it doesn't depend upon the value entered as N.
Therefore, the time taken can be written as


$$ T(N) = N^2 + 2 $$

However, as the value of N increases, the difference in time complexity due to the constant _2_ is negligible, therefore when we represent the time complexity of this program, we can write it as 

$$ O(N^2) $$

Say we modified the program such that there would be a printf statement in the loop,

```c
#include <stdio.h>
int main(){
    int N;
    printf("Enter the value of N:");
    scanf("%d",&N);
    int arr[N][N];
    for(int i=0;i<N;i++){
        for(int j=0;j<N;j++){
            arr[i][j]=i*N+j;
            printf("%d ",arr[i][j]);
        }
    }
    return 0;
}
```
Then the time taken would be represented as

$$ T(N) = 2 \times N^2 + 2 $$

However, we can ignore constants when finding the time complexity, even when they are multiplying a variable. Therefore, the time complexity would still be represented as

$$ O(N^2) $$

Since in time complexity $$k_{1}N^2$$ is basically $$N^2$$

Say we want to perform an action _N_ times.
```c
#include <stdio.h>
int main(){
    int N;
    printf("Enter the value of N:");
    scanf("%d",&N);
    int arr[N][N];
    for(int i=0;i<N;i++){
        printf("Row %d\n",i);
        for(int j=0;j<N;j++){
            arr[i][j]=i*N+j;
            printf("%d ",arr[i][j]);
        }
    }
    return 0;
}
```
We can see that ```printf("Row %d\n",i);``` is executed N times. Therefore, if we look at the time taken

$$T(N) = 2\times N^2 + N + 2 $$

However, we only look at the most dominant term in the equation, which is obviously $$N^2$$, so we can discard $$N$$. Therefore, the time complexity will still be

$$O(N^2)$$

Let's take another example

```c
#include <stdio.h>
int main(){
    int N;
    printf("Enter the value of N:");
    scanf("%d",&N);
    int arr[N];
    printf("Enter N values\n");
    for(int i=0;i<N;i++) scanf("%d",&arr[i]);
    for(int i=0;i<N-1;i++){
        for(int j=i+1;j<N;j++){
            printf("%d %d",arr[i],arr[j]);
        }
    }
}
```

What this program does is input a value of N, take in N integers, and print all the possible combinations. Let's say all the printf and scanf statements take _k_ time. We can say that the printf statement in the first for loop executes _N_ times, and the printf statement in the nested loop is executed $$\frac{N\times(N-1)}{2}$$ times. Therefore the time taken is


$$T(N) = \frac{N\times(N-1)}{2} + N + k = \frac{N^2}{2} - \frac{N}{2} + N + k$$

Which will be simplified to

$$O(N^2)$$

Therefore, even if the constant multiplying the dominant factor is less than one, we can still ignore it. Therefore, $$\frac{N^2}{2}$$ is simplified to $$k_{1}N^2$$ where $$k_{1} = \frac{1}{2}$$

Time complexity might not be as important while making small scale programs, where the inputs might not be very large. However, they are very important, when program optimization is priority and especially useful in Competitive Programming, where you can figure out if a certain algorithm's time complexity will be sufficient for a certain question, or if it requires a more efficient algorithm.
