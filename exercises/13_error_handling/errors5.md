# Boxing Errors

A way to write simple code while preserving the original errors is to `Box` them. The drawback is that the underlying error type is only known at runtime and not statically determined.

The stdlib helps in boxing errors by having `Box` implement conversion from any type that implements the `Error` trait into the trait object `Box<dyn Error>`, via `From`. This allows multiple different error types to be returned from the same function, since they're all boxed as trait objects.

Think of the `Box<dyn _>` type as an "I want anything that does _" type. For errors, the bound is the `Error` trait — so `Box<dyn Error>` means "some owned value whose only guarantee is that it implements `Error`." Any error type that implements `Error` (including custom enums that `impl Error for ...`) can flow into the same `Result<_, Box<dyn Error>>`, and `?` will perform the conversion automatically.

```rust
use std::error::Error;
use std::fs::File;
use std::io::Read;
use std::num::ParseIntError;

fn run() -> Result<(), Box<dyn Error>> {
    let mut f = File::open("number.txt")?;  // std::io::Error on failure
    let mut contents = String::new();
    f.read_to_string(&mut contents)?;
    let _n: i32 = contents.trim().parse()?;  // ParseIntError on failure
    Ok(())
}
```

The key advantage is simpler code that can handle multiple error types in one `Result`. The disadvantage is that you lose static type information — the specific error type is only known at runtime through dynamic dispatch, rather than being determined at compile time.

---

**References**

[1] Rust by Example — [Boxing errors](https://doc.rust-lang.org/rust-by-example/error/multiple_error_types/boxing_errors.html)
