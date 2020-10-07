# iiit-notebook

iiit-notebook is a public repository of notes taken by students of IIIT Hyderabad. 
The website itself is completely static, generated using Jekyll, and made by Pratyaksh Gautam.

## Features

The notes are automatically organised according to the course code and date.
The site has support for various features to improve note-taking such as

+ LaTeX embedded in `$...$` (inline) and `$$...$$` (display), using MathJax

+ Syntax highlighting for code using Rouge, 
```
\`\`\`language-name
    insert code here

\`\`\`
```
+ Graphs written in mermaid-js, simply by writing the code in a `mermaid` code block.

## Contributing

Clone this repository onto your device and `cd` into it:
```
git clone https://github.com/iiit-notebook/iiit-notebook.github.io
cd iiit-notebook.github.io
```

The notes themselves are located in the `_posts/` directory and follow the standard Jekyll naming format, `yyyy-mm-dd-title`
for eg: `_posts/2020-09-14-c-pro-lecture-1.md`

Write your notes in markdown format, with the following front matter for Jekyll at the start of the document.
```
---
title: C Pro Lecture 1
author: Pratyaksh Gautam
code: cs0.101
number: 1
---
```
## Downloading as PDF

You can download the notes and convert them into convenient PDF's to read offline as well. 
You must have `pandoc` and `texlive-full` installed on your system for this to work.

Download the .md file for the lecture you want from the `_posts` directory, for eg `2020-09-29-ds-lecture-7.md`.
```
pandoc 2020-09-29-ds-lecture-7.md -o ds-lecture-7.pdf
```
This creates a PDF file of the lecture notes, `ds-lecture-7.pdf`, in the same directory as the downloaded notes.
