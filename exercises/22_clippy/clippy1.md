# Standard Library Constants

Clippy identifies floating point literals that closely match constants
available in the standard library's `std::f32::consts` and `std::f64::consts`
modules, recommending the use of predefined constants instead.

The constants defined in Rust's standard library are typically more precise
than manually written approximations: "Usually, the definition in the standard
library is more precise than what people come up with."

Replace approximate literals with their corresponding standard library
constants to improve both accuracy and code clarity.
