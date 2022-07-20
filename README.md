# comparison
spaceship (`<=>`) operator simulation library for Go

## Requirements
- Go 1.18 or newer

## Installation
```bash
go get github.com/heucuva/comparison
```

## How to use
Import this library into your code:

```go
import "github.com/heucuva/comparison"
```

Then, you can easily add a comparable type like so:
```go
type ComparableString string

func (lhs ComparableString) Compare(rhs ComparableString) comparison.Spaceship {
	switch {
	case lhs < rhs:
		return comparison.SpaceshipRightGreater
	case lhs > rhs:
		return comparison.SpaceshipLeftGreater
	default:
		return comparison.SpaceshipEqual
	}
}

func Example() {
    // Here, we create two strings that are comparable using the spaceship operation
    a := ComparableString("aaaa")
    b := ComparableString("bbbb")

    // We expect the value in `a` to be less than the value in `b`
    // So we should get a value of `comparison.SpaceshipRightGreater`
    if a.Compare(b) == comparison.SpaceshipRightGreater {
        fmt.Println("You win!")
    } else {
        fmt.Println("Better luck next time!")
    }
}
```
