# Tuples and Destructuring

A *tuple* is a general way of grouping together a number of values with a variety of types into one compound type. Tuples have a fixed length: Once declared, they cannot grow or shrink in size.

We create a tuple by writing a comma-separated list of values inside parentheses. Each position in the tuple has a type, and the types of the different values in the tuple don't have to be the same.

```rust
let tup: (i32, f64, u8) = (500, 6.4, 1);
```

To get the individual values out of a tuple, we can use pattern matching to *destructure* a tuple value, which breaks the single tuple into multiple parts.

```rust
let tup = (500, 6.4, 1);
let (x, y, z) = tup;
println!("The value of y is: {y}");
```

---

**References**

[1] The Rust Programming Language — [Data Types](https://doc.rust-lang.org/book/ch03-02-data-types.html)
