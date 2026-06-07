# Type Parameters

Generics is the topic of generalizing types and functionalities to broader cases. The simplest and most common use of generics is for type parameters.

To parameterize a type, we name the type parameter, just as we do for value parameters. You can use any identifier as a type parameter name. By convention, type parameter names in Rust are short, often just one letter, and Rust's type-naming convention is UpperCamelCase. Short for *type*, `T` is the default choice of most Rust programmers.

```rust
fn largest<T: PartialOrd>(list: &[T]) -> &T {
    let mut largest = &list[0];
    for item in list {
        if item > largest {
            largest = item;
        }
    }
    largest
}
```

In most cases, the compiler is able to infer `T`, for example after pushing a value with a concrete type to a `Vec<T>`. When inference isn't enough, the type parameter can be supplied through a type annotation.

---

**References**

[1] The Rust Programming Language — [Generic Data Types](https://doc.rust-lang.org/book/ch10-01-syntax.html)
