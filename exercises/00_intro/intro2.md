# Formatted print

Printing is handled by a series of `macros` defined in `std::fmt` some of which are:

- `print!`: prints text to the console (io::stdout).
- `println!`: same as `print!` but a newline is appended.

```rust
// Basic placeholder
println!("{} days", 31);

// Positional arguments
println!("{0}, this is {1}. {1}, this is {0}", "Alice", "Bob");

// Named arguments
println!("{subject} {verb} {object}",
         subject="the quick brown fox",
         verb="jumps over",
         object="the lazy dog");

// Debug formatting
println!("{:?}", (3, true, "hello"));
println!("{:#?}", (3, true, "hello"));
```

---

**References**

[1] Rust by Example — [Formatted print](https://doc.rust-lang.org/rust-by-example/hello/print.html)
