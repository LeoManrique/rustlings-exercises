# For Loops Over Fallibles

Both `Option` and `Result` implement the `IntoIterator` trait, which allows
using them in a `for` loop. A `for` loop over `Option` or `Result` will iterate
either 0 (if the value is `None`/`Err(_)`) or 1 time (if the value is
`Some(_)`/`Ok(_)`). This is not very useful and is more clearly expressed via
`if let`.

A `for` loop can also be accidentally written with the intention to call a
function multiple times, while the function returns `Some(_)`; in these cases
a `while let` loop should be used instead.

The "intended" use of `IntoIterator` implementations for `Option` and `Result`
is passing them to generic code that expects something implementing
`IntoIterator`. For example using `.chain(option)` to optionally add a value
to an iterator.
