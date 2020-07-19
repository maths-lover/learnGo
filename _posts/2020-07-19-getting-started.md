---
title: Getting Started
date: 2020-07-19 18:50:21 +0530
categories: [Basics]
tags: [starting,basics,gobasics,basic,getting_started]
comments: false
pin: true
---

# Getting Started

## Basic structure

Look at the following codes, no need to understand anything, just have a glance at both.

#### Go
```go
package main

import "fmt"

func f1(a int) int {
  return 12 * a
}

func main() {
  fmt.Printf("12 * 12 = %d\n", f1(12))
  fmt.Printf("Hello, World!\n")
}
```

#### C
```c
#include <stdio.h>

int f1(int a) {
  return 12 * a;
}

int main() {
  printf("12 * 12 = %d\n", f1(12));
  printf("Hello, World\n");
  return 0;
}
```

1. `package` declares the package that code belongs to, while in C/C++ there is no such thing, but we accomplish that with header guards and header files in general.
2. `import "fmt"` is basically like `#include <stdio.h>` in C.
As `stdio.h` provides standard I/O operations, similarly that `fmt` provides formatted input/output in Go.
3. As you might have already caught on that both have a printf command and they are identical. Well yes, they are almost identical with `fmt.Printf()` having more features, which we'll see later.
4. Now coming to semicolons`;` we see them in `C` syntax but not in `Go` syntax. Although `Go` uses `;` just like C, but we don't have to put them, when compiling go compiler automatically puts them. As for reason why this? It's a long story.

## The one true brace style
Go follows the __one true brace style__ which is basically opening brace on same line as the `func` keyword, and closing brance on it's own line

__e.g.,__

```go
package main

import "fmt"

func main() { // notice this line, also this is inline comment same as C/C++
  fmt.Println("Hello")
}
```

#### History
When go was being developed `;` were literally everywhere, so in December 2009, some senior go devs
removed the necessity of semicolons in code and added a feature in compiler
to add `;` at the end of each line except the one with sepcefic keywords including `func`
which is why Go is picky about it's syntax, thought not as picky as python, etc.

Now for example have a look at the below snippet,
```go
func main()
{
}
```
This above snippet will produce errors because compiler will generate something like the following,
```go
func main()
{;
}
```
Which is syntax error and a big no-no
