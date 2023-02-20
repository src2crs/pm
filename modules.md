# Modules in Source2Course

The following is a description of some of Source2Course's central modules.
These are not the only modules that will be added, but they are the first
to be developed. For future modules, see the [ideas page](ideas.md).

## `fileparser`

A module for managing source files.
It provides types and functions for reading, writing, and parsing source files.
It is a central part of Source2Course and will be relied on by most other modules.

For example, this module can read a file and extract sections
that are defined using comments.
One possible use case is to read files containing exam assignments or submissions and
produce an exam, create a pdf version from what a student has submitted etc.

This module is language agnostic and doesn't expect a source file to be syntactically
correct. It only relies on the correct segmentation of the files, which is described
by a much simpler grammar than that of an actual programming language
(or maybe even regular expressions).

Thus, we cannot use a parser that is specific to a certain language.
This module has to be configurable for the language and use case.
I.e. there has to be a way to define section types, comment styles etc.
In the long run, there should be a grammar and a parser to read and process files.

## `goparser`

A specialized module for parsing go files.
This provides types and functions for parsing go source code and extracting functions,
structs etc. This will probably be a wrapper around go's parser package that also
exposes at least some parts of the `fileparser` module.

For example, it can extract a function with a given name, its description comment etc.
for use in slides or examples.
It can also be useful when grading exams by telling if a submission has syntax errors.

## `gorunner`

A module for running go source code.
This module can read and execute go code that has been extracted by the `goparser` or
`fileparser` modules.

The basic idea is that the `goparser` or `fileparser` modules should be used to extract
parts of source files and recombine them into code that can be executed using `gorunner`.
This can be used e.g. for executing test code when grading exams or visualising algorithms.
Besides executing code, the module may also provide statistical data, e.g. how many
of the tests succeed, fail, crash, or (don't) compile.

*Disclamer*:
One possible way of implementing this module is to have it generate tests and run them
using `go test`. Another possibility is to use an interpreter library like
[yaegi](https://github.com/traefik/yaegi) to accomplish this.
Either way, there will be **no security measures whatsoever!**
I.e. the code will not be run in a sandboxed environment nor are there any other
measures to prevent the code from manipulating the system Source2Course runs on.  

While security may be considered later, we will for now assume that the executed code is
trusted. As Source2Course is meant to be used by lecturers who process their own source
code or that of students whom they know in person, this is a reasonable assumption.
If in doubt, you can check the code to be run beforehand using a diff tool or the
facilities Source2Course provides, or maybe even consider running your students' code
inside e.g. a docker container or a virtual machine.
