# Testing for Panics

To check that your code handles error conditions as expected, you can use the `#[should_panic]` attribute. The test passes if the code inside the function panics; it fails if the code doesn't panic.

A `#[should_panic]` test can be imprecise — it passes if the code panics for any reason. To make tests more precise, add an optional `expected` parameter containing a substring of the panic message you expect:

```rust
#[test]
#[should_panic(expected = "less than or equal to 100")]
fn greater_than_100() {
    Guess::new(200);
}
```

The test runner verifies that the panic message contains the provided substring. This ensures the code panics for the specific reason you expect.
