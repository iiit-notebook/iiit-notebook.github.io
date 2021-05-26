---
title: CL1 Lecture 2
author: Pratyaksh Gautam
date: 2021-05-26
code: cl3.101
number: 2
---

## Model of Language Processing

 Inputs -> Lexical Processing <-> Syntactic Processing <-> Semantic Processing <-> Discourse Processing -> Outputs

 This process occurs with reference to the general knowledge of the lexicon, syntactic rules, semantic rules,
 and discourse rules.
 Note the two directional arrows, we cannot simply view the process as a uni directional flow.
 We may have to come back to earlier stages of the process in order to get an accurate output.

 Consider the two sentences
 > "The building blocks are made of plastic"
 > "The building blocks the sun"

 In the first sentence the word 'blocks' acts as a noun, and in the second, as a verb.
 If we greedily classify the word 'blocks' to the first match, and never come back to lexically reanalyze the token,
 we would be stuck with an inaccurate meaning for the word given the context.
