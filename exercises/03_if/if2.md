# Handling Multiple Conditions with `else if`

You can use multiple conditions by combining `if` and `else` in an `else if` expression. When this program executes, it checks each `if` expression in turn and executes the first body for which the condition evaluates to `true`. Once it finds one, it doesn't even check the rest.

Using too many `else if` expressions can clutter your code, so if you have more than one, you might want to refactor your code.

Because each arm produces the function's result, every arm must yield the same type. Bare string literals have type `&'static str`, so they can be returned directly without any extra reference or borrow.
