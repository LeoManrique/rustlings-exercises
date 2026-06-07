# Arrays

Another way to have a collection of multiple values is with an *array*. Unlike a tuple, every element of an array must have the same type. Unlike arrays in some other languages, arrays in Rust have a fixed length.

```rust
let a = [1, 2, 3, 4, 5];
let a: [i32; 5] = [1, 2, 3, 4, 5];
let first = a[0];
```

Arrays are useful when you want your data allocated on the stack or when you want to ensure that you always have a fixed number of elements. An array is a single chunk of memory of a known, fixed size that can be allocated on the stack.

A common shorthand initializes every slot with the same value by writing the value, a semicolon, and the length inside square brackets.

```rust
let a = [3; 5]; // equivalent to [3, 3, 3, 3, 3]
```

---

**References**

[1] The Rust Programming Language — [Data Types](https://doc.rust-lang.org/book/ch03-02-data-types.html)
