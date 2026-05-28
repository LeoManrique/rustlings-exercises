# Iterator Adapters and `collect`

*Iterator adapters* are methods that don't consume the iterator. Instead, they produce different iterators by changing some aspect of the original iterator.

The `map` method takes a closure to call on each item as items are iterated through, returning a new iterator that produces modified items:

```rust
let v1: Vec<i32> = vec![1, 2, 3];
v1.iter().map(|x| x + 1);
```

However, this code produces a warning because iterators are lazy and do nothing unless consumed. To fix this, use the `collect` method, which consumes the iterator and collects the resultant values into a collection data type:

```rust
let v2: Vec<_> = v1.iter().map(|x| x + 1).collect();
assert_eq!(v2, vec![2, 3, 4]);
```

You can chain multiple calls to iterator adapters to perform complex actions in a readable way. Because all iterators are lazy, you must call one of the consuming adapter methods to get results.

`collect` is generic over the collection it returns, so it can build different types — for example, a `Vec<String>`, or a `String` by gathering characters or pieces.
