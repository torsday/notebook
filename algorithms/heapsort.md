# Heapsort

*From: [Wikipedia](https://en.wikipedia.org/wiki/Heapsort)*

> A comparison-based sorting algorithm. Heapsort can be thought of as an improved selection sort: like that algorithm, it divides its input into a sorted and an unsorted region, and it iteratively shrinks the unsorted region by extracting the largest element and moving that to the sorted region. The improvement consists of the use of a heap data structure rather than a linear-time search to find the maximum.

> Although somewhat slower in practice on most machines than a well-implemented quicksort, it has the advantage of a more favorable worst-case O(n log n) runtime. Heapsort is an in-place algorithm, but it is not a stable sort.

![Heapsort Gif](https://upload.wikimedia.org/wikipedia/commons/1/1b/Sorting_heapsort_anim.gif)

## Steps

1.  Call the buildMaxHeap() function on the list. Also referred to as heapify(), this builds a heap from a list in O(n) operations.
1.  Swap the first element of the list with the final element. Decrease the considered range of the list by one.
1.  Call the siftDown() function on the list to sift the new first element to its appropriate index in the heap.
1.  Go to step (2) unless the considered range of the list is one element.

## References

-   [Wikipedia: Heapsort](https://en.wikipedia.org/wiki/Heapsort)
