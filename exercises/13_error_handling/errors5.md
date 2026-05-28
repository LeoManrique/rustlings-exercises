# Boxing Errors

A way to write simple code while preserving the original errors is to `Box` them. The drawback is that the underlying error type is only known at runtime and not statically determined.

The stdlib helps in boxing errors by having `Box` implement conversion from any type that implements the `Error` trait into the trait object `Box<dyn Error>`, via `From`. This allows multiple different error types to be returned from the same function, since they're all boxed as trait objects.

Think of the `Box<dyn _>` type as an "I want anything that does _" type. For errors, the bound is the `Error` trait — so `Box<dyn Error>` means "some owned value whose only guarantee is that it implements `Error`." Any error type that implements `Error` (including custom enums that `impl Error for ...`) can flow into the same `Result<_, Box<dyn Error>>`, and `?` will perform the conversion automatically.

The key advantage is simpler code that can handle multiple error types in one `Result`. The disadvantage is that you lose static type information — the specific error type is only known at runtime through dynamic dispatch, rather than being determined at compile time.
