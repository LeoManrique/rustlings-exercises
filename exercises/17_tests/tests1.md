# Test Anatomy and `assert!`

Tests are Rust functions that verify that non-test code is functioning in the expected manner. The bodies of test functions typically perform three actions:

1. Set up any needed data or state
2. Run the code you want to test
3. Assert that the results are what you expect

At its simplest, a test in Rust is a function annotated with the `#[test]` attribute. To change a function into a test function, add `#[test]` on the line before `fn`. When you run tests with the `cargo test` command, Rust builds a test runner binary that runs the annotated functions and reports whether each test passes or fails.

The `#[cfg(test)]` attribute on the module indicates that this code should only be compiled when running tests. Non-test functions can exist in the `tests` module to help set up common scenarios or perform common operations, so you must always annotate actual test functions with `#[test]` to indicate which functions the test runner should treat as tests.

The `tests` module is an inner module that follows normal visibility rules, so you need an import like `use super::*;` to access the code you're testing.

```rust
pub fn add(left: u64, right: u64) -> u64 {
    left + right
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn it_works() {
        let result = add(2, 2);
        assert_eq!(result, 4);
    }
}
```

The `assert!` macro ensures that some condition in a test evaluates to `true`. If the value is `true`, nothing happens and the test passes. If the value is `false`, the macro calls `panic!` to cause the test to fail. `assert_eq!` and `assert_ne!` test equality and inequality respectively, and print both values on failure to make debugging easier.

---

**References**

[1] The Rust Programming Language — [How to Write Tests](https://doc.rust-lang.org/book/ch11-01-writing-tests.html)
