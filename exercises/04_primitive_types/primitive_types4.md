# Slices

*Slices* let you reference a contiguous sequence of elements in a collection. A slice is a kind of reference, so it does not have ownership.

We create slices using a range within square brackets by specifying `[starting_index..ending_index]`, where *starting_index* is the first position in the slice and *ending_index* is one more than the last position in the slice. Internally, the slice data structure stores the starting position and the length of the slice, which corresponds to *ending_index* minus *starting_index*.
