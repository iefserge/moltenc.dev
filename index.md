---
layout: page
title: Evolved C programming language
nav_order: 1
nav_title: Home
---
![Molten C]({{site.url}}/logo.svg){:width="200px"}

# __Molten C__ -- evolved C programming language

This is a project to create an improved version of C, explore
an alternative data-oriented evolution path for C. The goal is to preserve
an essence and "spirit" of C, and seamlessly
interoperate with C libraries of any complexity, including C standard library.

#### Factorial

```
Int fact(Int n) {
  if (n == 0)
    return 1

  return n * fact(n - 1)
}

print(fact(5)) // 120
```

#### C Interop

```
extern library "c"
import library "stdio.h" {
  printf
}

export Int main() {
  printf("Hello, World!\n") // Hello, World!
  return 0
}
```

#### Optionals

```
Bool hasPositive(Int ?x, Int ?y) {
  return ?x && x > 0 || ?y && y > 0
}

print(hasPositive(1, 1))     // true
print(hasPositive(1, null))  // true
print(hasPositive(null, 1))  // true
print(hasPositive(null, -1)) // false
```

#### Sum Types

```
enum Animal {
  elephant {Int weight}
  lion
}

Bool isDangerous(Animal a) {
  switch (a) {
  case .lion:
    return true
  case .elephant{weight}:
    return weight > 3000
  }
}

print(isDangerous(.elephant{weight = 12000})) // true
print(isDangerous(.elephant{weight = 1000}))  // false
print(isDangerous(.lion))                     // true
```

#### Raw Pointers

```
extern library "c"
extern var *raw malloc(Int size)
extern Int32 puts(Byte *raw)
extern var Byte *raw strdup(Byte *raw)

var Byte *raw *raw values = malloc(sizeof(Byte *raw) * 2)
values[0] = strdup("foo")
values[1] = null

for (var p = values; *p != null; p++) {
  puts(*p) // "foo"
}
```

## Compatibility with C

Molten C is not source compatible with C,
but compiler can import C headers and interoperate with C libraries.
This is possible because Molten C can parse C code and convert C headers
on the fly. Code in this language can be integrated into C projects
file-by-file.

## Applications

This is a "non-object-oriented" language, more aligned with
data-oriented design paradigm.
There are no classes, interfaces or type behaviors in the language.
It goes another direction, featuring fully structural type system with
support for opaque types for data hiding.

The name __Molten C__ can mean various things:

- reforged C
- language that is not SOLID
- yet another language inspired by C

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


---

[Tweet about this &#x2192;](https://twitter.com/intent/tweet?text={{ site.twitter_text | escape }}&url={{ site.url }}{{ site.baseurl }}){: .btn }
