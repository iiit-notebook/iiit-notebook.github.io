---
title: CL 1 Lecture 3 notes
author: Pratyaksh Gautam
date: 2021-05-31
code: cl3.101
number: 3
---

## A simple architecture of a Machine Translation System

```
(Flow of data: top to bottom)

Source Languge Analysis
------------------------
| Preprocessors
| Font convertors
| Identifying idioms,
| collocations, phrasal verbs, etc.


| POS Tagger

| Morphological Analyzer

| Chunker

| Parser

Source Language - Target Language mapping
-------------------------------------------

| Transfer Rules
| Preposition mapping rules
| Word sense disambiguation
| Bidix lookup

Target Language Generator
--------------------------
| Morphological Generator
| Sentence Generator
| Font convertors
```

In agglutinative languages such as Dravidian languages like Telugu,
we may prefer to run the Morphological analyser before the POS tagger.
