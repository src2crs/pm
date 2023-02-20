# Ideas for Source2Course

## Create LaTeX code from source files

This was the original idea for Source2Course:
A lecturer should be able to define examples, code snippets, explanations, or even
complete slide sets etc. in actual source files that can be automatically tested.
From these files, Source2Course should create LaTeX sources (or other documentation),
ensuring that the examples used in slides are not outdated and do not fail their tests.

You may see this as a kind of literate programming tailored towards education.
Besides extracting source code and creating documents from it, Source2Course should
also be able to extract the output of a function or ensure certain tests are ok
when creating the docs.

## Create exams or assignments from templates

Exams or assignments should be provided in the form of source files that contain
tasks, solutions, hints etc.
From these templates, assignments can be generated that contain only a part of the
original contents.

## Parse and run source code for grading exams

Extract source code from test and/or submissions handed in by students.
Recombine these code snippets to produce tests that can be run and evaluated to assist
in grading.

## Augment code with additional functions

The idea is to have "regular" source code in a repo that is tested and easily readable.
It should not contain any unnecessary function calls or comments that can be distracting
or mistaken by students to be a part of the algorithm.

However, algorithms or data structures can be visualized e.g. by executing additional
code every time a function is called or a data structure is accessed, producing
a trace, log, or drawing an image while the code is running.
To this end, an interpreter could be used that executes source code that has been
augmented with additional commands.
