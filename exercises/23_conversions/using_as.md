# Type Casting with `as`

The simplest form of type conversion is a type cast expression. It is denoted with the binary operator `as`. For instance, `println!("{}", 1 + 1.0);` would not compile, since `1` is an integer while `1.0` is a float. However, `println!("{}", 1 as f32 + 1.0)` should compile.

```rust
let n = 1 as f32 + 1.0; // integer cast to float before addition
let c = 65u8 as char;   // numeric value cast to the corresponding character ('A')
```

Note that the `as` operator is not only used when type casting. It also helps with renaming imports.

```rust
use std::io::Result as IoResult;
```

---

**References**

[1] The Rust Standard Library — [std::convert](https://doc.rust-lang.org/std/convert/index.html)
