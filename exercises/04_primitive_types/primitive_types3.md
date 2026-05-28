# Arrays

Another way to have a collection of multiple values is with an *array*. Unlike a tuple, every element of an array must have the same type. Unlike arrays in some other languages, arrays in Rust have a fixed length.

Arrays are useful when you want your data allocated on the stack or when you want to ensure that you always have a fixed number of elements. An array is a single chunk of memory of a known, fixed size that can be allocated on the stack.

A common shorthand initializes every slot with the same value by writing the value, a semicolon, and the length inside square brackets.
