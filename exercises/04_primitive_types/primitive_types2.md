# The Character Type

Rust's `char` type is the language's most primitive alphabetic type. We specify `char` literals with single quotation marks, as opposed to string literals, which use double quotation marks. Rust's `char` type is 4 bytes in size and represents a Unicode scalar value, which means it can represent a lot more than just ASCII. Accented letters; Chinese, Japanese, and Korean characters; emojis; and zero-width spaces are all valid `char` values in Rust. Unicode scalar values range from `U+0000` to `U+D7FF` and `U+E000` to `U+10FFFF` inclusive.
