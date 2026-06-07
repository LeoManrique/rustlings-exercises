# Choosing Between Borrowing and Taking Ownership

Designing a function means deciding whether its parameter should be owned or borrowed.

Taking ownership and returning ownership with every function is tedious. References let a function use a value without transferring ownership, so the caller keeps it:

```rust
fn calculate_length(s: &String) -> usize {
    s.len()
}
```

The action of creating a reference is called *borrowing*. When you're done, you have to give it back. You don't own it.

If a function only needs to look at a value, take it by reference. If a function needs to consume, replace, or otherwise take possession of a value, take it by value:

```rust
fn consume(mut data: String) {
    data = data.to_uppercase();
    println!("{data}");
}
```

At the call site, an owned argument is passed as-is; a borrow is created with `&` (or `&mut`). The choice between `&T` and `T` is made on each parameter independently.

---

**References**

[1] The Rust Programming Language — [References and Borrowing](https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html)
