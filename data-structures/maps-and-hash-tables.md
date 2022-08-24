# Hash Table
1) A hash table consists of two major components, a bucket array and a hash function.
2) A bucket array is an array of size N, where each cell is thought of as a bucket, a collection of key-value pairs.
3) If the keys are integers in range [0, N-1], this bucket array is all that is needed. An entry e with key k would simply be inserted into the k-th cell of the array.
4) Otherwise, we need a hash function.
5) One could simply create an array of size N for key value pairs with keys ranging from 0 to N-1. (in which case, both insertion and deletion are O(1)) However, if the number of key-value pairs are much smaller than N, this would be a waste of space.

# Hash Function
1) A hash function is an irreversible function that produces a seemingly arbitrary value from its input. 

2) We could use the hash function to map the original keys to each of the buckets (indexes of the array).

3) When an arbitrary object is put into a hash function, first it will produce a hash code (which the integer value need not to be in the range of [0, N-1])
   
4) Then the hash code will be mapped to a range of [0, N-1] via a compression function.


# Hash Code
1) For C++, we could simply interpret the input data type (`char`, `short`, `long`, etc.) as integers. But for data types that have more bits than `int` types, you can sum up the higher order bits and the lower order bits in order to match the size of `int` and produce better hashing (by taking into account all the bits).

2) Polynomical hash codes, Cyclic shift hash codes are used to further avoid unwanted collisions for `char` or `string` or other viarable-length objects.

# Compression Function
1) Modulo of the size of the bucket array.
h(k) = |k| mod N
2) MAD method (multiply add and divide)
- h(k) = |ak + b| mod N
- a and b are nonnegative integers randomly chosen at the time the compression function is determined.