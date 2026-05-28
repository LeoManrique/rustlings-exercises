# Almost Swapped

Clippy detects a common mistake in variable assignment: patterns like
`a = b; b = a;` which appear to be failed swap attempts.

"This looks like a failed attempt to swap." The code compiles but doesn't
accomplish the intended behavior — after these assignments, both variables
end up with the same value.

When swapping is actually intended, use `std::mem::swap(&mut a, &mut b);`
instead. It swaps the values at two mutable locations, without deinitializing
either one, and clearly expresses the swapping intent.

This lint helps catch logic errors that might otherwise go unnoticed since
the code won't produce compiler errors — only incorrect runtime behavior.
