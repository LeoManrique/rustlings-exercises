# Exporting Macros from Modules

A `macro_rules!` macro defined inside a module is, by default, only
usable within that module. To make it available to code outside the
module where it is defined, an annotation is needed that indicates the
macro should be made available whenever the surrounding scope is brought
into view. Without this annotation, the macro can't be brought into
scope.

The relevant attribute is `#[macro_export]`, placed directly above the
`macro_rules!` definition.
