# Mutability

By default, variables are immutable. Once a value is bound to a name with `let`, you can't change that value. Trying to assign to it a second time produces a compile-time error:

```
error[E0384]: cannot assign twice to immutable variable `x`
```

It's important that we get compile-time errors when we attempt to change a value that's designated as immutable, because this very situation can lead to bugs. If one part of our code operates on the assumption that a value will never change and another part of our code changes that value, it's possible that the first part of the code won't do what it was designed to do.

You can opt in to mutability by adding `mut` in front of the variable name:

```rust
let mut x = 5;
x = 6;
```

Adding `mut` also conveys intent to future readers of the code by indicating that other parts of the code will be changing this variable's value.
