# iiit-notebook

iiit-notebook is a public repository of notes taken by students of IIIT Hyderabad. 
The website itself is completely static, generated using Jekyll.

## Features

The notes are automatically organised according to the course code and date.
The site has support for various features to improve note-taking such as

+ LaTeX embedded in `$...$` (inline) and `$$...$$` (display), using MathJax

+ Syntax highlighting for code using Rouge, 
<pre>
```c
	printf("Hello, world!\n");
```
</pre>
+ Graphs written in mermaid-js, simply by writing the code in a `mermaid` code block.

## Contributing

Fork this repository onto your device and `cd` into it:
```
git clone https://github.com/<your-username>/iiit-notebook.github.io
cd iiit-notebook.github.io
```

The notes themselves are located in the `_posts/` directory and follow the standard Jekyll naming format, `yyyy-mm-dd-title`
for eg: `_posts/2020-09-14-c-pro-lecture-1.md`

Write your notes in markdown format, with the following front matter for Jekyll at the start of the document. This is some example front matter, edit it accordingly.
```
---
title: C Pro Lecture 1
author: Pratyaksh Gautam
code: cs0.101
number: 1
---
```

After that, you can add, commit and push your repo, and then make a PR to merge your changes.

### Compatibility between `pandoc` and `jekyll`

The website itself uses jekyll, but the PDF's rendered by `pandoc` generally look better and are more preferable, however not everything is perfectly compatible between the two, especially in math mode.
When writing your notes keep the following things in mind:

1. If you need to have pipe symbols (`\|`) or curly brackets (`\{`), not only should you escape them as shown here, but also nest them in a `div`. If you don't do this jekyll (the site) probably won't render it properly.  
For inline math: `<div>$S = \{a, b\}$</div>`  
For display math:
```
<div>
$$f(x) = \|2 \times x + 1\|$$
</div>
```

2. `pandoc` doesn't take kindly to spacing in between math mode delimiiters.  
This works:
```
$\frac{a}{b}$
```
This might not:
```
$ \frac{a}{b} $
```

### Courses

Sometimes you might be the first person to write notes for a certain course, and as a result, the course itself will not exist as part of the website.
You will have to add the course manually in that case. Simply make a file titled `course-code.md` in the `_courses/` directory. See below example:

```
---
code: cs0.101
name: Computer Programming
lecturer: Prof. Suresh Purini
---
Introductory course to computer programming.
```

## Downloading as PDF

You can download the notes and convert them into convenient PDF's to read offline as well. 
You must have `pandoc` and `texlive-full` installed on your system for this to work.
Use the pandoc mermaid filter if you wish to have the graphs rendered as well.

Download the .md file for the lecture you want from the `_posts` directory, for eg `2020-09-29-ds-lecture-7.md`.
```
pandoc 2020-09-29-ds-lecture-7.md -o ds-lecture-7.pdf
```
This creates a PDF file of the lecture notes, `ds-lecture-7.pdf`, in the same directory as the downloaded notes.
