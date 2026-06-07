# Generic Structs

We can also define structs to use a generic type parameter in one or more fields using the `<>` syntax. The syntax for using generics in struct definitions is similar to that used in function definitions. First, we declare the name of the type parameter inside angle brackets just after the name of the struct. Then, we use the generic type in the struct definition where we would otherwise specify concrete data types.

```rust
struct Point<T> {
    x: T,
    y: T,
}
```

We can implement methods on structs and use generic types in their definitions too. Note that we have to declare `T` just after `impl` so that we can use `T` to specify that we're implementing methods on the type. By declaring `T` as a generic type after `impl`, Rust can identify that the type in the angle brackets is a generic type rather than a concrete type.

```rust
impl<T> Point<T> {
    fn x(&self) -> &T {
        &self.x
    }
}

let p = Point { x: 5, y: 10 };
println!("p.x = {}", p.x());
```

---

**References**

[1] The Rust Programming Language — [Generic Data Types](https://doc.rust-lang.org/book/ch10-01-syntax.html)
