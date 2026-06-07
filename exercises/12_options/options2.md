# `if let` and `while let`

For some use cases, when matching enums, `match` is awkward. `if let` is cleaner for this use case and in addition allows various failure options to be specified.

The `if let` construct reads: "if `let` destructures the value into the given pattern, evaluate the block."

```rust
if let Some(i) = letter {
    println!("Matched {:?}!", i);
}
```

## `while let`

Similar to `if let`, `while let` can make awkward `match` sequences more tolerable. It allows you to destructure a pattern within a loop condition. If the destructuring succeeds, the loop body executes; if it fails, the loop breaks automatically. This eliminates excessive indentation and the need to explicitly handle the failing case compared to using `match` in a loop.

```rust
while let Some(i) = optional {
    // ...
}
```

You can do nested pattern matching in `if let` and `while let` statements, which is useful when a value such as `Vec::pop()` adds another layer of `Option`.

---

**References**

[1] Rust by Example — [if let](https://doc.rust-lang.org/rust-by-example/flow_control/if_let.html)

[2] Rust by Example — [while let](https://doc.rust-lang.org/rust-by-example/flow_control/while_let.html)
