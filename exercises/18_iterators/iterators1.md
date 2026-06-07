# The Iterator Trait and `next`

All iterators implement a trait named `Iterator` that is defined in the standard library:

```rust
pub trait Iterator {
    type Item;

    fn next(&mut self) -> Option<Self::Item>;

    // methods with default implementations elided
}
```

The `Iterator` trait only requires implementors to define one method: `next`, which returns one item of the iterator at a time wrapped in `Some`, and returns `None` when iteration is over.

When calling the `next` method on iterators directly, note that you must make the iterator mutable, as calling `next` changes internal state to keep track of where it is in the sequence. In other words, this code *consumes*, or uses up, the iterator.

The `iter` method produces an iterator over immutable references.

---

**References**

[1] The Rust Programming Language — [Processing a Series of Items with Iterators](https://doc.rust-lang.org/book/ch13-02-iterators.html)
