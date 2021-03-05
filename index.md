---
layout: page
title: Evolved C programming language
nav_order: 1
nav_title: Home
---
![Molten C]({{site.url}}/logo.svg){:width="200px"}

# __Molten C__ -- evolved C programming language

Systems programming language that attempts to evolve the C language,
exploring data-oriented evolution path for C.

Language allows seamless interop with C libraries of any complexity,
including the C standard library. Although very similar, the language is not compatible
with C on the source code level, but C libraries can be imported and used directly.

#### Clean and refined syntax

Minimal changes to the C syntax, "modern" conveniences like optional
commas in newline-separated lists, optional parentheses around conditionals and
optional semicolons.
At the same time, clearly misleading or ambiguous constructs are disallowed.

```swift
Int fact(Int n) {
  if n == 0 {
    return 1
  }

  return n * fact(n - 1)
}

print(fact(5)) // 120
```

#### Module system and C integration

Explicit imports and exports prevent global namespace name collisions and
allow for faster incremental compilation. Each Molten C file is a module and
isolated namespace. Build system that discovers and links all files and
libraries together is built-in into compiler and requires no configuration.

C header files can be seamlessly imported, with no need to create
wrapper libraries or "bindings".

```clean
import "stdio.h" {printf}

export Int main() {
  printf("Hello, World!\n") // Hello, World!
  return 0
}
```

#### Expressive and safe

Optional types allow `null` to be assigned to variables of any type and
allow compiler to diagnose unchecked usage of `null` at compile time.

```swift
Bool hasPositive(Int ?x, Int ?y) {
  return ?x && x > 0 || ?y && y > 0
}

print(hasPositive(1, 1))     // true
print(hasPositive(1, null))  // true
print(hasPositive(null, 1))  // true
print(hasPositive(null, -1)) // false
```

Extended enumeration type works like a tagged union, it can hold additional
data that is embedded into cases. Pattern matching is supported and compiler
can verify exhaustiveness of `switch` statements, where all possible cases must
be handled.

```swift
enum Animal {
  elephant {Int weight}
  lion
}

Bool isLargeElephant(Animal a) {
  switch a {
  case .lion:
    return false
  case .elephant {weight}:
    return weight > 3000
  }
}

print(isLargeElephant((.elephant){.weight = 12000})) // true
print(isLargeElephant((.elephant){.weight = 1000}))  // false
print(isLargeElephant(.lion))                        // false
```

#### Raw Pointers And Memory Access

All features of the C language, including raw pointers, manual
memory allocation, bitfields and unions.

```swift
import "stdlib.h" {malloc, free}
import "stdio.h" {puts}
import "string.h" {strdup}

export Int main() {
  var Byte *raw *raw values = malloc(sizeof(Byte *raw) * 2)
  values[0] = strdup("foo")
  values[1] = null

  for var auto p = values; *p != null; p++ {
    puts(*p) // "foo"
    free(p)
  }
  
  free(values)
  return 0
}
```

## Compatibility with C

Molten C syntax is not a superset of C,
but the compiler can import C headers and interoperate with C libraries.
This is possible because Molten C can parse C code and convert C headers
on the fly. Code in Molten C can be integrated into C projects
one file at a time.

## Applications

This is a "non-object-oriented" language, much more aligned with
the data-oriented design paradigm.
There are no classes, interfaces or type behaviors in the language.
It uses another approach, featuring fully structural type system with
support for opaque types for data hiding.

The name Molten C can mean various things:

- reforged C
- language that is not SOLID
- yet another language inspired by C

Molten C is not a general purpose program language, but it attempts
to be really good for:

- software with low latency or memory requirements
- low level software like operating systems or hardware drivers
- graphics software like renderers or games
- WebAssembly programs that need to be small in size

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

## Yet another new language?

Molten C attempts to preserve the "spirit" of C, evolving it into more
expressive and safe C. Data-oriented design paradigm had a large influence on
the design of the language.

## Project Status

Compiler has been in development since 2018. It went through
multiple full and partial rewrites and a number of experiments.

Source code is not publicly available yet. A few
important features and refinements are missing and need to be done before the
initial release. Current open-source release estimate is late 2021.

## Author

|---|---|
|![Serge](https://avatars1.githubusercontent.com/u/6034700?s=460&v=4){:width="60px" style="border-radius:10px;margin-right:1rem;"}|**Sergii Iefremov (Serge)**<br>[Github](https://github.com/iefserge) [Twitter](https://twitter.com/iefserge)|


---

[Tweet about this &#x2192;](https://twitter.com/intent/tweet?text={{ site.twitter_text | escape }}&url={{ site.url }}{{ site.baseurl }}){: .btn }
