---
title: Demon that devours thy RAM
date: 2020-07-22 03:23:13 +0530
categories: [Basics]
tags: [ioutil,basics,read,files]
comments: false
pin: true
---

# The `ioutil` package
Let's begin with the solution to previous challenge about reading whole file in one gulp.

> dup3.go

```go
package main

import (
  "fmt"
  "io/ioutil"
  "os"
  "strings"
)

func main() {
  counts := make(map[string]int)
  for _, filename := range os.Args[1:] {
    data, err := ioutil.ReadFile(filename)
    if err != nil {
      fmt.Fprintf(os.Stderr, "dup3: %v\n", err)
      continue
    }
    for _, line := range strings.Split(string(data), "\n") {
      counts[line]++
    }
  }
  for line, n := range counts {
    if n > 1 {
      fmt.Printf("%d:  %s\n", n, line)
    }
  }
}
```

So here insteaad of reading the file line by line we read the whole file in one go (storing it in RAM)
then split the line and proceeded with our task.

In `dup2.go` we did something like,
```go
file, err := os.Open(filename)
if err != nil {
  panic("Given file is messed up.")
}
while(file.Scan()) {
  // do some tasks here with the line that is just scanned
}
file.Close()
```

while in `dup3.go` we're doing something like,
```go
file, err := ioutil.Readfile(filename)
if err != nil {
  panic("Your file is messed up")
}
for index, str := range strings.Split(string(file), "\n") { // Note: we can give any sorts of delimiter here
                                                          // Like even just a space, " " or something like
                                                          // "\t" or like "s" etc.
  // Do some task here with index and str
}
```

You might have already thought of this, but `strings.Split()` is exact opposite of what `strings.Join()` is.


Under the covers all `bufio.Scanner()`, `ioutil.ReadFile()`, `ioutil.WriteFile` use the `Read` and `Write`
methods of `*os.File`, but we don't have to use them, as `bufio` and `ioutil` are far easier to work with.
