# Equality Assertions

A common way to verify functionality is to test for equality between the result of the code under test and the expected value. The `assert_eq!` macro compares two arguments for equality, while `assert_ne!` compares two arguments for inequality.

These macros print the values if the assertion fails, making it easier to see why the test failed. When an `assert_eq!` test fails, it prints output like:

```
assertion `left == right` failed
  left: 5
 right: 4
```

The `assert_eq!` and `assert_ne!` macros use the operators `==` and `!=`, respectively, and require that the values being compared implement the `PartialEq` and `Debug` traits. You can derive these traits on custom structs and enums with `#[derive(PartialEq, Debug)]`.
