# Renaming with `as`

The `use` keyword creates a shortcut to a path, allowing you to use a shorter name instead of writing out the full path repeatedly. Adding `use` and a path in a scope is similar to creating a symbolic link in the filesystem. Paths brought into scope with `use` also check privacy like any other paths.

When bringing items into scope, use `as` to create an alias — a new local name for the path. This prevents naming conflicts and lets you choose a name that fits the surrounding code while keeping the original definition untouched:

```rust
use std::fmt::Result;
use std::io::Result as IoResult;
```

Within a module, relative paths can start with `self` to refer to the current module, so an alias like `use self::child::ITEM as NEW_NAME;` rebinds a child-module item under a new name in the current scope.
