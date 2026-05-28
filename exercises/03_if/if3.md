# Using `if` in a `let` Statement

Because `if` is an expression, we can use it on the right side of a `let` statement to assign the outcome to a variable.

Remember that blocks of code evaluate to the last expression in them, and numbers by themselves are also expressions. This means the values that have the potential to be results from each arm of the `if` must be the same type. If the types are mismatched, we'll get an error. The expression in the `if` block must evaluate to the same type as the expression in the `else` block, because variables must have a single type, and Rust needs to know definitively at compile time what type the variable is.
