# ezwp
Easy-to-use,  no-dep, generic-based worker pool implementation, written in Go 1.18
# Installation
```
go get -u github.com/h1ght1me/ezwp
```
# Usage
```
package main

import (
	"fmt"
	"github.com/h1ght1me/ezwp"
)

func main() {
	wp := ezwp.New[int, string](
		ezwp.Options[int, string]{
			Payload: func(i int) (string, error) {
				return fmt.Sprint(i), nil
			},
		},
		[]int{1, 2, 3, 4, 5},
	)

	for r := range wp.Run() {
		fmt.Println(r)
	}
}
```