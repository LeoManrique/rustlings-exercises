# Statements and Expressions

Function bodies are made up of a series of statements optionally ending in an expression. Because Rust is an expression-based language, this is an important distinction to understand.

- _Statements_ are instructions that perform some action and do not return a value.
- _Expressions_ evaluate to a resultant value.

Calling a function is an expression. Calling a macro is an expression. A new scope block created with curly brackets is an expression. A math operation like `5 + 6` is an expression that evaluates to `11`.

**Important:** expressions do not include ending semicolons. If you add a semicolon to the end of an expression, you turn it into a statement, and it will then not return a value.

In Rust, the return value of a function is synonymous with the value of the final expression in the block of the body of the function. You can return early with the `return` keyword, but most functions return the last expression implicitly:

```rust
fn square(num: i32) -> i32 {
    num * num
}
```

If you place a semicolon at the end of that final line, you change it from an expression into a statement, the function no longer produces a value, and you get a type-mismatch error against the declared return type.
