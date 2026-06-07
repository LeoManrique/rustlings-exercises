# Tuple Indexing

We can access a tuple element directly by using a period (`.`) followed by the index of the value we want to access. As with most programming languages, the first index in a tuple is 0.

```rust
let tup: (i32, f64, u8) = (500, 6.4, 1);
let five_hundred = tup.0;
let six_point_four = tup.1;
let one = tup.2;
```

---

**References**

[1] The Rust Programming Language — [Data Types](https://doc.rust-lang.org/book/ch03-02-data-types.html)
