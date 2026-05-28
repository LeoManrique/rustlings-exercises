# The `match` Control Flow Construct

Rust has an extremely powerful control flow construct called `match` that allows you to compare a value against a series of patterns and then execute code based on which pattern matches. The power of `match` comes from the expressiveness of the patterns and the fact that the compiler confirms that all possible cases are handled.

A `match` expression consists of arms. An arm has two parts: a pattern and some code. The pattern is compared against the value being matched, and if it matches, the associated code is executed. When the `match` expression executes, it compares the resultant value against the pattern of each arm, in order. If a pattern matches the value, the code associated with that pattern is executed; otherwise execution continues to the next arm.

Match arms can also bind to the parts of the values that match the pattern. This is how you can extract values out of enum variants. The pattern to destructure an enum corresponds to the way the data stored within the enum is defined. For struct-like enum variants, you can use a pattern similar to the one you specify to match structs. For tuple-like enum variants, the pattern is similar to the one you specify to match tuples. The number of variables in the pattern must match the number of elements in the variant you're matching. For variants without any data, you can only match on the literal value, and no variables are in that pattern.

The arms' patterns must cover all possibilities. Matches in Rust are *exhaustive*: you must exhaust every last possibility in order for the code to be valid. If you don't handle all possible cases, the compiler will produce an error and prevent compilation.

Sources: <https://doc.rust-lang.org/book/ch06-02-match.html>, <https://doc.rust-lang.org/book/ch19-03-pattern-syntax.html>
