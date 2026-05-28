# Identifying `&str` vs `String`

String literals are stored as string slices (`&str`) in the program's binary.
A `String` is produced by methods and macros that allocate an owned,
UTF-8 encoded buffer:

- `String::from(...)` — explicit construction
- `.to_string()` — available on types implementing `Display`
- `.to_owned()` — converts a borrowed `&str` into an owned `String`
- `.into()` — converts when the target type (`String`) can be inferred
- `format!(...)` — works like `println!` but returns a `String`

Methods that return owned data produce a `String` (for example, `replace` and
`to_lowercase`), while methods that return a view into existing data — such as
`trim` or slicing with `&s[a..b]` — produce a `&str`.

Slicing uses byte indices, not character indices. Character indexing can be
done using `s.chars().nth(INDEX)`.
