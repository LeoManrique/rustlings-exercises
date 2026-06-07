# Mapping an Iterator into a Vector

`map()` transforms one iterator into another by applying a closure to each
element. It takes a closure and creates an iterator which calls that closure
on each element of the original iterator.

If you are good at thinking in types, you can think of `map()` like this: if
you have an iterator that gives you elements of some type `A`, and you want
an iterator of some other type `B`, you can use `map()`, passing a closure
that takes an `A` and returns a `B`.

`map()` is conceptually similar to a `for` loop. However, as `map()` is lazy,
it is best used when you're already working with other iterators. Calling
`.collect()` at the end consumes the lazy iterator and produces a concrete
collection, such as a `Vec<T>`.

```rust
let a = [1, 2, 3];
let doubled: Vec<i32> = a.iter().map(|x| 2 * x).collect();
```

If you're doing some sort of looping for a side effect, it's considered more
idiomatic to use `for` than `map()`.

---

**References**

[1] The Rust Standard Library — [Iterator::map](https://doc.rust-lang.org/std/iter/trait.Iterator.html#method.map)
