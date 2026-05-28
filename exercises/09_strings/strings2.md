# Borrowing a `String` as `&str`

When a function takes a string slice and you have a `String`, you can pass a
reference to the `String`. The compiler performs deref coercion, converting
`&String` to `&str` automatically.

This is the same mechanism that makes the `+` operator on strings work: its
`add` method has the signature `fn add(self, s: &str) -> String`, yet you can
pass `&String` for the second parameter because of deref coercion.
