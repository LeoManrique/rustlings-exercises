# `filter` and Flattening Nested Iterators

Many iterator adapters take closures as arguments. The `filter` method takes a closure that gets an item from the iterator and returns a `bool`. If the closure returns `true`, the value will be included in the iteration produced by `filter`. If it returns `false`, the value won't be included.

Closures used with iterator adapters commonly capture their environment — for example, comparing each item against a value from the surrounding scope:

```rust
shoes.into_iter().filter(|s| s.size == shoe_size).collect()
```

Here the closure captures `shoe_size` from its environment and uses it to filter the iterator.

Once filtered, a consuming adapter like `count` (which calls `next` until exhaustion and returns how many items it saw) reduces the result to a single number.

When the source is a sequence of sequences (for example, a slice of maps, each yielding its own values iterator), `flat_map` turns each outer item into an inner iterator and concatenates them into one flat stream. Equivalently, `map(...).flatten()` produces the same effect. This lets a single chain of adapters traverse a nested structure without an outer loop.
