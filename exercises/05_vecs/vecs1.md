# Creating a Vector with the `vec!` Macro

Vectors (`Vec<T>`) are Rust's first collection type, allowing you to store
multiple values of the same type in a single data structure with all values
positioned next to each other in memory.

To create an empty vector, call the `Vec::new` function. Since no initial
values are inserted, you must add a type annotation so Rust knows what element
type to expect. The `Vec<T>` type provided by the standard library can hold
any type, and you specify it within angle brackets.

More commonly, you'll create a vector with initial values. Rust conveniently
provides the `vec!` macro, which creates a new vector holding the values you
give it:

```rust
let v = vec![1, 2, 3];
```

Because initial `i32` values are provided, Rust infers that `v` is `Vec<i32>`,
so the type annotation isn't necessary. The integer type defaults to `i32`
unless otherwise specified.

---

**References**

[1] The Rust Programming Language — [Storing Lists of Values with Vectors](https://doc.rust-lang.org/book/ch08-01-vectors.html)
