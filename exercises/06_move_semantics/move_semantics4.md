# Mutable References and Non-Overlapping Scopes

A mutable reference lets a function modify a borrowed value:

```rust
fn change(some_string: &mut String) {
    some_string.push_str(", world");
}
```

Mutable references have one big restriction: if you have a mutable reference to a value, you can have no other references to that value. This restriction prevents data races at compile time.

A reference's scope, however, starts from where it is introduced and continues through the last time that reference is used — not all the way to the end of the enclosing block. So two mutable references to the same value can coexist in the same block, as long as the first one is finished being used before the second one is created:

```rust
let mut x = Vec::new();
let y = &mut x;
y.push(1);
// y is no longer used after this point, so its borrow has ended.
let z = &mut x;
z.push(2);
```

The order of statements matters: each use of a reference extends its live scope.

---

**References**

[1] The Rust Programming Language — [References and Borrowing](https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html)
