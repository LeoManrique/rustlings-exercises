# Variants with Associated Data

Rather than putting an enum inside a struct, we can put data directly into each enum variant. Each variant can have different types and amounts of associated data.

```rust
enum Message {
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}
```

This enum has four variants with different types:

- `Quit`: Has no data associated with it at all
- `Move`: Has named fields, like a struct does
- `Write`: Includes a single `String`
- `ChangeColor`: Includes three `i32` values

Defining an enum with variants such as these is similar to defining different kinds of struct definitions, except the enum doesn't use the `struct` keyword and all the variants are grouped together under a single type.

Just as we're able to define methods on structs using `impl`, we're also able to define methods on enums. The body of the method would use `self` to get the value that we called the method on.

Source: <https://doc.rust-lang.org/book/ch06-01-defining-an-enum.html>
