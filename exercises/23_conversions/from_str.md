# The `FromStr` Trait

The `std::str` module offers a trait called `FromStr` which helps with converting strings into target types via the `parse` method on strings. Upon implementing `FromStr`, you can use the `parse` method on strings to generate an object of the implementor type.

```rust
pub trait FromStr: Sized {
    type Err;
    fn from_str(s: &str) -> Result<Self, Self::Err>;
}
```

### Required components

1. **Associated type `Err`** — specifies the error type returned when parsing fails.
2. **Method `from_str`** — parses a string slice and returns `Result<Self, Self::Err>`.

If properly implemented for a given type `Person`, then `let p: Person = "Mark,20".parse().unwrap()` should both compile and run without panicking.

The expected input format depends on the specific type's implementation. A type's `FromStr` implementation may not accept the same format as its `Display` implementation; even if it does, the `Display` output may not be lossless, causing information loss during round-tripping.

### Usage

```rust
use std::str::FromStr;

let s = "5";
let x = i32::from_str(s).unwrap();
assert_eq!(5, x);
```

The following three calls are equivalent:

```rust
Point::from_str("(1,2)")
"(1,2)".parse()
"(1,2)".parse::<Point>()
```
