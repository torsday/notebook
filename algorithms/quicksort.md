# Quicksort

Quicksort first divides a large array into two smaller sub-arrays: the low elements and the high elements, then recursively sorts the sub-arrays.

## Steps

1.  Pick an element, called a pivot, from the array.
1.  Partitioning: reorder the array so that all elements with values less than the pivot come before the pivot, while all elements with values greater than the pivot come after it (equal values can go either way). After this partitioning, the pivot is in its final position. This is called the partition operation.
1.  Recursively apply the above steps to the sub-array of elements with smaller values and separately to the sub-array of elements with greater values.

The base case of the recursion is arrays of size zero or one, which never need to be sorted.

## Notes

-   Sometimes called partition-exchange sort.
-   Is a comparison sort,
-   A divide & conquer algorithm.
-   In efficient implementations *it is not* a stable sort.
-   Can operate in-place on an array, requiring small additional amounts of memory to perform the sorting.
-   When implemented well, it can be about two or three times faster than its main competitors, merge sort and heapsort.

![Quicksort Gif](https://upload.wikimedia.org/wikipedia/commons/6/6a/Sorting_quicksort_anim.gif)

| x                           | y                                                                          |
|-----------------------------|----------------------------------------------------------------------------|
| Class                       | Sorting algorithm                                                          |
| Worst case performance      | O(n2)                                                                      |
| Best case performance       | O(n log n) (simple partition) or O(n) (three-way partition and equal keys) |
| Average case performance    | O(n log n)                                                                 |
| Worst case space complexity | O(n) auxiliary (naive), O(log n) auxiliary (Sedgewick 1978)                |


The pivot selection and partitioning steps can be done in several different ways; the choice of specific implementation schemes greatly affects the algorithm's performance.

-   Lomuto partition scheme
-   Hoare partition scheme

## Examples

```ruby
def quicksort(array, from=0, to=nil)
    if to == nil
        # Sort the whole array, by default
        to = array.count - 1
    end

    if from >= to
        # Done sorting
        return
    end

    # Take a pivot value, at the far left
    pivot = array[from]

    # Min and Max pointers
    min = from
    max = to

    # Current free slot
    free = min

    while min < max
        if free == min # Evaluate array[max]
            if array[max] <= pivot # Smaller than pivot, must move
                array[free] = array[max]
                min += 1
                free = max
            else
                max -= 1
            end
        elsif free == max # Evaluate array[min]
            if array[min] >= pivot # Bigger than pivot, must move
                array[free] = array[min]
                max -= 1
                free = min
            else
                min += 1
            end
        else
            raise "Inconsistent state"
        end
    end

    array[free] = pivot

    quicksort array, from, free - 1
    quicksort array, free + 1, to
end
```

## References

-   [gist: aspyct/sort.rb](https://gist.github.com/aspyct/3433278)
-   [Wikipedia: Quicksort](https://en.wikipedia.org/wiki/Quicksort)
