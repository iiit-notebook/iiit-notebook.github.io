---
title: DSM Lecture 7
date: 2021-03-05
author: Pratyaksh Gautam
code: ec2.101
number: 7
---

## Standard logic gates
Of the boolean logic functions possible, we only consider a few of them as **standard** logic gates, owing to practical reasons.  
- We do not consider any of the unary operations, such as NOT
- The inhibition and implication functions are not associative or commutative, thus we do not consider them either.

The AND, OR, NOT, XOR, NAND, NOR 

### Universal gates
The NAND and the NOR gates are known as **universal gates**, any logic gate can be constructed using either one of these gates.
We can show this by implementing NOT, AND and OR gates, which are known as the *basic gates*. If we can implement these basic gates,
then we can implement any digital circuit.

- **NOT**: For a signal $x$, we can get $x'$ by doing either $(x.x)'$ or $(x.1)'$.  
- **AND**: Now that we have a NOT gate, we can implement AND by putting this NOT gate after the AND gate, giving us $((x.y)')'$ = $(x.y)$.  
- **OR**: Using DeMorgan's law, we know that $(x.y)' = (x' + y')$. We can use this fact to generate and OR gate as follows $(x'.y')' = ((x')' + (y')') = (x + y).  

### Timing diagrams
The horizontal axis in a timing diagram represents the time, and the vertical axis shows the signal as it changes between the two possible voltage levels. By interpreting the signal as the output values of a truth table, this information can be carried in the signal.

## Logic circuits
### 2 bit binary adder
