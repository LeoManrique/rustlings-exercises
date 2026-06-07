# Shadowing

You can declare a new variable with the same name as a previous variable. Rustaceans say that the first variable is _shadowed_ by the second, which means that the second variable is what the compiler will see when you use the name of the variable. In effect, the second variable overshadows the first, taking any uses of the variable name to itself until either it itself is shadowed or the scope ends.

We shadow a variable by repeating the use of the `let` keyword with the same name:

```rust
let x = 5;
let x = x + 1;
```

Shadowing is different from marking a variable as `mut` because we'll get a compile-time error if we accidentally try to reassign to this variable without using the `let` keyword. By using `let`, we can perform a few transformations on a value but have the variable be immutable after those transformations have completed.

The other difference between `mut` and shadowing is that because we're effectively creating a new variable when we use the `let` keyword again, we can change the type of the value but reuse the same name:

```rust
let spaces = "   ";
let spaces = spaces.len();
```

The first `spaces` variable is a string type, and the second `spaces` variable is a number type. Shadowing thus spares us from having to come up with different names. With `mut`, by contrast, the compiler would reject changing the type, reporting "mismatched types".

---

**References**

[1] The Rust Programming Language — [Variables and Mutability](https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html)
