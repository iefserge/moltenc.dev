---
layout: page
title: Molten C
nav_order: 1
---
# __Molten C__ -- yet another "systems" programming language

__Molten C__ is a modern low-level non-object-oriented programming language based on C.
Unlike other similar languages, Molten C attempts to preserve as much C syntax,
semantics and "spirit" as possible while making language more pleasant and easy to use.

__Molten C__ is not source compatible with C,
but it can import C headers and seamlessly interoperate with C libraries of any complexity.

---

#### Factorial

```swift
Int fact(Int n) {
  if (n == 0)
    return 1

  return n * fact(n - 1)
}

trace fact(5) // 120
```

#### C interop and printf

```swift
import "stdio.h" {
  printf
}

Int main() {
  printf("Hello, World!\n") // "Hello, World!"
  return 0
}
```

#### Optionals (nullable types)

```swift
atLeastOnePositiveNumber(Int ?x, Int ?y) {
  trace (?x && x > 0 || ?y && y > 0) ? "found" : "nope"
}

atLeastOnePositiveNumber(1, 1)     // "found"
atLeastOnePositiveNumber(1, null)  // "found"
atLeastOnePositiveNumber(null, 1)  // "found"
atLeastOnePositiveNumber(null, -1) // "nope"
```

#### Enum (Algebraic data types)

```swift
enum Animal {
  elephant {Int weight}
  lion
}

Bool isLarge(Animal animal) {
  switch (animal) {
  case .lion:
    return false
  case .elephant{weight}:
    return weight > 10000
  }
}

trace isLarge(.elephant{weight = 12000}) // true
trace isLarge(.elephant{weight = 6000})  // false
trace isLarge(.lion)                     // false
```

#### Raw Pointers

```swift
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

---

Read more [about Molten C]({{ '/about' | absolute_url }}).

---

[Tweet about this &#x2192;](https://twitter.com/intent/tweet?text={{ site.twitter_text | escape }}&url={{ site.url }}{{ site.baseurl }}){: .btn.btn-blue }
