# Reference-Counted Multiple Ownership

In the majority of cases, ownership is clear: You know exactly which variable owns a given value. However, there are cases when a single value might have multiple owners. For example, in graph data structures, multiple edges might point to the same node, and that node is conceptually owned by all of the edges that point to it. A node shouldn't be cleaned up unless it doesn't have any edges pointing to it and so has no owners.

You have to enable multiple ownership explicitly by using the Rust type `Rc<T>`, which is an abbreviation for _reference counting_. The `Rc<T>` type keeps track of the number of references to a value to determine whether or not the value is still in use. If there are zero references to a value, the value can be cleaned up without any references becoming invalid.

We use the `Rc<T>` type when we want to allocate some data on the heap for multiple parts of our program to read and we can't determine at compile time which part will finish using the data last.

Every time we call `Rc::clone`, the reference count to the data within the `Rc<T>` will increase, and the data won't be cleaned up unless there are zero references to it. The implementation of `Rc::clone` doesn't make a deep copy of all the data like most types' implementations of `clone` do. The call to `Rc::clone` only increments the reference count, which doesn't take much time.

When we create a value with `Rc::new`, the count starts at 1; each call to `clone` increases it by 1. We don't have to call a function to decrease the reference count: The implementation of the `Drop` trait decreases the reference count automatically when an `Rc<T>` value goes out of scope. The current count can be observed with `Rc::strong_count`.

Note that `Rc<T>` is only for use in single-threaded scenarios.

```rust
use std::rc::Rc;

let a = Rc::new(5);
let b = Rc::clone(&a);
let c = Rc::clone(&a);

println!("count after creating a = {}", Rc::strong_count(&a)); // 3
drop(c);
println!("count after dropping c = {}", Rc::strong_count(&a)); // 2
```

---

**References**

[1] The Rust Programming Language — [Rc, the Reference Counted Smart Pointer](https://doc.rust-lang.org/book/ch15-04-rc.html)
