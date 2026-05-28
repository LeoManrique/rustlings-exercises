# Creating a New Hash Map

The `HashMap<K, V>` type stores a mapping of keys of type `K` to values of type `V` using a hashing function, which determines how it places these keys and values into memory.

Hash maps are useful when you want to look up data not by using an index, as you can with vectors, but by using a key that can be of any type.

One way to create an empty hash map is to use `new` and to add elements with `insert`. You need to first `use` the `HashMap` from the collections portion of the standard library. Of the three common collections, this one is the least often used, so it's not included in the features brought into scope automatically in the prelude. Hash maps also have less support from the standard library; there's no built-in macro to construct them, for example.

Just like vectors, hash maps store their data on the heap. Like vectors, hash maps are homogeneous: All of the keys must have the same type, and all of the values must have the same type.
