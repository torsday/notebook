# Binary Search Algorithm

*From: [Wikipedia](https://en.wikipedia.org/wiki/Binary_search_algorithm)*

> a binary search or half-interval search algorithm finds the position of a target value within a **sorted array**. The binary search algorithm can be classified as a dichotomic divide-and-conquer search algorithm and executes in logarithmic time.

| x                           | y        |
|-----------------------------|----------|
| Data structure              | Array    |
| Worst case performance      | O(log n) |
| Best case performance       | O(1)     |
| Average case performance    | O(log n) |
| Worst case space complexity | O(1)     |

![Binary Search GIF](http://darcy.rsgc.on.ca/ACES/ICS3U/images/BinarySearchAnimation.gif)

## Example

```ruby
def binary_search(array, value, from=0, to=nil)
    if to == nil
        to = array.count - 1
    end

    mid = (from + to) / 2

    if value < array[mid]
        return binary_search array, value, from, mid - 1
    elsif value > array[mid]
        return binary_search array, value, mid + 1, to
    else
        return mid
    end
end
```
