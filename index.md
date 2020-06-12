---
layout: page
title: Molten C
nav_order: 1
nav_title: Home
---
# __Molten C__

__Molten C__ is _yet another_ system programming language based on C.
It attempts to preserve core C syntax and "spirit"
while making language more expressive and pleasant to use.

__Molten C__ is not a superset of C,
but compiler can import and seamlessly interoperate with C libraries of
any complexity.

---

#### Factorial

```
Int fact(Int n) {
  if (n == 0)
    return 1

  return n * fact(n - 1)
}

trace fact(5) // 120
```

#### C interop and printf

```
import library "c"
import "stdio.h" {
  printf
}

Int main() {
  printf("Hello, World!\n") // Hello, World!
  return 0
}
```

#### Optionals (nullable types)

```
Bool hasPositive(Int ?x, Int ?y) {
  return ?x && x > 0 || ?y && y > 0
}

trace hasPositive(1, 1)     // true
trace hasPositive(1, null)  // true
trace hasPositive(null, 1)  // true
trace hasPositive(null, -1) // false
```

#### Enum (sum types)

```
enum Animal {
  elephant {Int weight}
  lion
}

Bool isDangerous(Animal animal) {
  switch (animal) {
  case .lion:
    return true
  case .elephant{weight}:
    return weight > 3000
  }
}

trace isDangerous(.elephant{weight = 12000}) // true
trace isDangerous(.elephant{weight = 1000})  // false
trace isDangerous(.lion)                     // true
```

#### Raw Pointers

```
import library "c"
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

[Tweet about this &#x2192;](https://twitter.com/intent/tweet?text={{ site.twitter_text | escape }}&url={{ site.url }}{{ site.baseurl }}){: .btn }
