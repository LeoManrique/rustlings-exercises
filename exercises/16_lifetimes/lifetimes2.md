# Dangling References and Borrow Scope

The main aim of lifetimes is to prevent dangling references — references
to data that has been deallocated. Rust's compiler contains a **borrow
checker** that compares scopes to determine whether all borrows are
valid. It analyzes the lifetimes of references to ensure they don't
outlive the data they reference.

If a value goes out of scope while a reference to it still exists in an
outer scope, the reference would point at memory that was deallocated.
The compiler rejects this with an error stating that the value "does not
live long enough."

A reference is valid as long as it ends before the lender is destroyed.
When a returned reference is tied (via lifetime annotations) to multiple
inputs, the lifetime of that reference equals the smaller of the input
lifetimes — so any use of the returned reference must fit inside the
scope of the shortest-lived input.
