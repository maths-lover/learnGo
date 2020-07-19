---
title: Setup of go
date: 2020-07-19 08:15:02 +0530
categories: [Basics]
tags: [setup,starting,basics,gobasics,basic]
comments: false
pin: true
---

# Installation

## Via package manager

First check wheter your package manager already provides go.

##### Debian and it's derivatives
```shell
sudo apt install go
```

##### Fedora and similar redhat based
```shell
sudo dnf install go
```

## Via tar ball
```shell
mkdir -pv ~/Downloads
pushd ~/Downloads # pushd is shell specefic if doesn't work then use cd
wget https://golang.org/dl/go1.14.6.linux-amd64.tar.gz
sudo tar -xzvf go1.14.6.linux-amd64.tar.gz -C /usr/local/go
```
If using bash then append in `~/.profile` or `~/.bash_profile` and if zsh then in `~/.zprofile`
```shell
export PATH=${PATH}:/usr/local/go/bin
```

and lastly execute the following.
```shell
source ~/.profile # or ~/.zprofile
```

Check your go installation
```shell
cat > test.go << "EOF"
package main

import "fmt"

func main() {
  fmt.Println("Hello, world!")
}
```

Then run the program
```
go run test.go
```
It should print `Hello, world!`

Don't forget to cleanup
```shell
rm test.go
```
