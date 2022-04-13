---
title: (lang-tasks) go -Fibonacci Sequence
---

```go
package main

import "fmt"

func printFib(num int) {
	a := 0
	b := 1
	c := b
	fmt.Printf("Series is %d %d", a, b)
	for {
		c = b
		b = a + b
		if b >= num {
			fmt.Println()
			break
		}
		a = c
		fmt.Printf(" %d", b)
	}
}

func main() {
	// display first 10 numbers
	printFib(10)
}
```
