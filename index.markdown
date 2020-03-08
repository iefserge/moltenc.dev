---
layout: home
---
# __rk__ -- yet another "systems" programming language

## Introduction

__rk__ (pronounced /ärk/ like arc) is a modern low-level programming language based on C.
Unlike other similar languages, rk attempts to preserve as much C syntax,
semantics and spirit as possible while making language more pleasant and easy to use.

Probably the best way to introduce programming language is to show code examples:

#### Factorial

```swift
Int fact(Int n) {
  if (n == 0)
    return 1

  return n * fact(n - 1)
}

trace fact(5) // prints "120"
```

#### Printf

```swift
import "stdio.h" {printf}

Int main() {
  printf("Hello, World!\n")   // prints "Hello, World!"
}
```

#### Option

```swift
bothPositiveNumbers(Int ?x, Int ?y) {
  trace (?x && x > 0 || ?y && y > 0) ? "yes" : "no"
}

trace bothPositiveNumbers(1, 1)    // prints "yes"
trace bothPositiveNumbers(1, null) // prints "no"
trace bothPositiveNumbers(null, 1) // prints "no"
```

#### Enum

```swift
enum Animal {
  elephant {Int weight}
  lion
}

Bool isTooHeavy(Animal animal) {
  switch (animal) {
  case .lion:
    return false
  case .elephant{weight}:
    return weight > 10000
  }
}

trace isTooHeavy(.elephant{weight = 12000}) // prints "true"
trace isTooHeavy(.elephant{weight = 6000})  // prints "false"
trace isTooHeavy(.lion)                     // prints "false"
```

#### Pointers

```swift
extern var *raw malloc(Int size)
extern Int32 puts(Byte *raw)
extern var Byte *raw strdup(Byte *raw)

var Byte *raw *raw values = malloc(sizeof(Byte *raw) * 2)
values[0] = strdup("foo")
values[1] = null

for (var p = values; *p != null; p++)
  puts(*p)   // prints "foo"
```

It is not fully source compatible with C, as a few breaking changes had to be made to
"modernize" it and make language more safe to use. This doesn't mean existing code
needs to be rewritten, since __rk__ is binary compatible with C. This way C
and rk code can be linked together and run side by side in the same program.

In fact, C libraries can be directly imported and used without any "bindings".
The core idea is to build on top of C, not replace it.

In addition, this is not an object oriented language, there are no classes,
protocols or behaviors. It's more aligned with the
[data-oriented design](https://en.wikipedia.org/wiki/Data-oriented_design) paradigm.
Code is compiled directly to machine code and doesn't use a garbage collector.

To be continued...
