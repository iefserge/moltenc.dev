---
layout: page
title: Evolved C programming language
nav_order: 1
nav_title: Home
---
![Molten C]({{site.url}}/logo.svg){:width="200px"}

# __Molten C__ -- evolved C programming language

__Molten C__ is a data-oriented programming language built to improve upon the C language, exploring
another alternative evolution path for C.

__Molten C__ follows the same underlying principles as C, in an attempt to preserve the "spirit" and essence of C.

__Molten C__ embraces the natural flow of data transformed from inputs into outputs, instead of modeling the world as interconnected entities (objects).

__Molten C__ supports seamless interoperation with existing C libraries of any complexity, including C standard library. Although, language is not a source code superset of C, it's possible to transparently import and use any C libraries.

### Example: Factorial

Minimal changes to the core C syntax:

```swift
Int fact(Int n) {
  if (n == 0)
    return 1

  return n * fact(n - 1)
}

print(fact(5)) // 120
```

### Example: C Interop

Module system with explicit imports and exports, which supports C header files:

```clean
import "stdio.h" {printf}

export Int main() {
  printf("Hello, World!\n") // Hello, World!
  return 0
}
```

### Example: Optionals

Nullable types, checked by the compiler:

```swift
Bool hasPositive(Int ?x, Int ?y) {
  return ?x && x > 0 || ?y && y > 0
}

print(hasPositive(1, 1))     // true
print(hasPositive(1, null))  // true
print(hasPositive(null, 1))  // true
print(hasPositive(null, -1)) // false
```

### Example: Sum Types

Tagged unions and pattern matching:

```swift
enum Animal {
  elephant {Int weight}
  lion
}

Bool isLargeElephant(Animal a) {
  switch (a) {
  case .lion:
    return false
  case .elephant{weight}:
    return weight > 3000
  }
}

print(isLargeElephant((.elephant){.weight = 12000})) // true
print(isLargeElephant((.elephant){.weight = 1000}))  // false
print(isLargeElephant(.lion))                        // false
```

### Example: Raw Pointers

Full power of the C language with raw pointers and manual memory allocation:

```swift
import "stdlib.h" {malloc, free}
import "stdio.h" {puts}
import "string.h" {strdup}

export Int main() {
  var Byte *raw *raw values = malloc(sizeof(Byte *raw) * 2)
  values[0] = strdup("foo")
  values[1] = null

  for (var auto p = values; *p != null; p++) {
    puts(*p) // "foo"
    free(p)
  }
  
  free(values)
  return 0
}
```

## Compatibility with C

Molten C has its own syntax and is not a superset of C,
but the compiler can import C headers and interoperate with C libraries.
This is possible because Molten C can parse C code and convert C headers
on the fly. Code in Molten C can be integrated into C projects
file-by-file.

## Applications

This is a "non-object-oriented" language, more aligned with
data-oriented design paradigm.
There are no classes, interfaces or type behaviors in the language.
It uses another approach, featuring fully structural type system with
support for opaque types for data hiding.

The name __Molten C__ can mean various things:

- reforged C
- language that is not SOLID
- yet another language inspired by C

Molten C is not a general purpose program language, but it attempts
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
It's hard to say when this happens, but current estimate is early 2021.

## Author

|---|---|
|![Serge](https://avatars1.githubusercontent.com/u/6034700?s=460&v=4){:width="80px" style="border-radius:10px;margin-right:1rem;"}|**Sergii Iefremov (Serge)**<br>[Github](https://github.com/iefserge) [Twitter](https://twitter.com/iefserge)|


---

[Tweet about this &#x2192;](https://twitter.com/intent/tweet?text={{ site.twitter_text | escape }}&url={{ site.url }}{{ site.baseurl }}){: .btn }
