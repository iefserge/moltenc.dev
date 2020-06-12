---
layout: page
title: About Molten C
permalink: /about
nav_order: 2
---
# About Molten C

![Molten C]({{site.url}}/logo.svg){:width="200px"}

__Molten C__ is a project to create an improved version of C, explore
an alternative evolution path for C, divergent from C++, Objective-C or
other languages in this space.
The goal is to preserve an essence and "spirit" of C, and build on top of
existing libraries, including C standard library.

__Molten C__ is not source compatible with C,
but compiler can import C headers and seamlessly interoperate with C libraries.
This is possible because Molten C can compile C code and convert C headers
on the fly. Code in this language can be integrated into C projects
file-by-file.

This is a "non-object-oriented" language, more aligned with
data-oriented design paradigm.
There are no classes, interfaces or type behaviors in the language.
It goes another direction, featuring fully structural type system with
support for opaque types for data hiding.

The name __Molten C__ can mean various things:

- reforged C
- unusable version of C
- language that is not SOLID
- yet another language that has "C" in its name

This language is not the best language for many programs, but it attempts
to be really good for:

- software with low latency or memory requirements
- low level software like operating systems or hardware drivers
- graphics software like renderers or games
- WebAssembly programs

## Implementation

Molten C compiler is written in C and depends on [LLVM](http://llvm.org/) for
code generation. This allows it to generate fast code and rich debug
information.

To support excellent C interop, compiler includes separate parsers for
C and Molten C languages, as well as C
preprocessor. Both parsers generate the same AST nodes. This
allows any C headers to be imported into Molten C, which means
Molten C compiler can compile arbitrary C source code.

There is an additional intermediate IR, that is similar to LLVM IR,
but more high level. In the future, code analysis and
optimization passes can be added.

## Project Status

Compiler has been in development since 2018. It went through
multiple full and partial rewrites and a number of experiments.

Source code is not publicly available yet. There are a few
important missing features and refinements that need to be done before the
initial release.
It's hard to say when this happens, but current estimate is sometime
during fall 2020.

## Author

|---|---|
|![Serge](https://avatars1.githubusercontent.com/u/6034700?s=460&v=4){:width="80px" style="border-radius:10px;margin-right:1rem;"}|**Sergii Iefremov (Serge)**<br>[Github](https://github.com/iefserge) [Twitter](https://twitter.com/iefserge)|

