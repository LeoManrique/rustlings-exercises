# Consuming Adapters

Methods that call `next` are called *consuming adapters* because calling them uses up the iterator. The `sum` method is an example: it takes ownership of the iterator, iterates through items by repeatedly calling `next`, adds each item to a running total, and returns the total when iteration is complete. After calling a consuming method like `sum`, you cannot use the iterator again.

`product` is the multiplicative counterpart: it multiplies every item together and returns the result. For the general case where you need a custom accumulation, `fold` takes an initial value and a closure that combines the accumulator with each item.

A `Range` such as `1..=n` is itself an iterator, so these reducers can be applied directly to a range without first materializing a collection:

```rust
let total: u64 = (1..=5).sum();      // 15
let factorial: u64 = (1..=5).product(); // 120
```
