---
layout: page
title: About Molten C
permalink: /about
nav_order: 2
---
# About Molten C

![Molten C]({{site.url}}/logo.svg){:width="200px"}

__Molten C__ is a project to create an improved version of C, explore
an alternative evolution path for C, divergent from C++, Objective-C or other
languages in that space.
The goal is to preserve an essence and "spirit" or C, and build on top of
its existing libraries including standard library. Replacing C is an
explicit non-goal.

__Molten C__ is not source compatible with C,
but it can import C headers and seamlessly interoperate with C libraries. This
is possible because Molten C can compile C code and "transpile" C headers on the fly.
Language can be integrated into C projects file-by-file.

This is also explicitly non-object-oriented language, and more aligned with
data oriented design paradigm.
There are no classes, interfaces or type behaviors in the language. It goes another direction,
featuring fully structural type system with opt-in opaque types for data hiding.

The name __Molten C__ can mean different things:

- C shaped into something "nicer"
- C needlessly shaped into something completely useless
- extremely hot and liquified version of C

This language is not the best language for all kinds of programs, but it attempts
to be really good for:

- software with low latency or memory requirements
- low level software like operating systems, drivers
- graphics software like renderers or games
- WebAssembly things

## Implementation

Molten C compiler is written in C and depends on [LLVM](http://llvm.org/) for
code generation. This allows it to generate very fast code and support
rich debug information.

To support excellent C interop, compiler includes separate parsers for
C and Molten C languages, as well as C
preprocessor. Both parsers generate the same AST nodes. This
allows not only any C headers to be imported into Molten C, but also
Molten C compiler to compile arbitrary C source code.

There is an additional intermediate IR, that is very similar to LLVM IR,
but a little more high level. In the future, code analysis and
optimization passes can be
added, to minimize the work that LLVM needs to do.

## Project Status

Compiler has been in development since 2018. It went through
multiple full and partial rewrites and experiments.

Source code is not publicly available yet. There are a few
important missing features and refinements that need to be done before the
initial release.
It's hard to say when this happens, but current estimate is sometime
around summer or fall 2020.

## Author

|---|---|
|![Serge](https://avatars1.githubusercontent.com/u/6034700?s=460&v=4){:width="80px" style="border-radius:10px;margin-right:1rem;"}|**Sergii Iefremov (Serge)**<br>[Github](https://github.com/iefserge) [Twitter](https://twitter.com/iefserge)|

