# Hash table

*From: [Wikipedia](https://en.wikipedia.org/wiki/Hash_table)*

> A data structure used to implement an associative array, a structure that can map keys to values. A hash table uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found.

> Ideally, the hash function will assign each key to a unique bucket, but it is possible that two keys will generate an identical hash causing both keys to point to the same bucket. Instead, most hash table designs assume that hash collisions—different keys that are assigned by the hash function to the same bucket—will occur and must be accommodated in some way.

> In a well-dimensioned hash table, the average cost (number of instructions) for each lookup is independent of the number of elements stored in the table. Many hash table designs also allow arbitrary insertions and deletions of key-value pairs, at (amortized) constant average cost per operation.

> In many situations, hash tables turn out to be more efficient than search trees or any other table lookup structure. For this reason, they are widely used in many kinds of computer software, particularly for associative arrays, database indexing, caches, and sets.

---

## References

-   [Algorithms, 4th Edition](http://algs4.cs.princeton.edu/34hash)
-   [StackOverflow: Hash tables VS associative arrays](http://stackoverflow.com/questions/3134296/hash-tables-vs-associative-arrays)
-   [Wikipedia: Hash Table](https://en.wikipedia.org/wiki/Hash_table)
-   [YouTube: What is a HashTable Data Structure - Introduction to Hash Tables , Part 0](https://www.youtube.com/watch?v=MfhjkfocRR0)
