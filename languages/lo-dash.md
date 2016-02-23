# Lo-Dash

## Basics

### Array Methods

```javascript
_.chunk(array, [size=0]) // Creates an array of elements split into groups the length of size
_.chunk(['a', 'b', 'c', 'd'], 2);

_.compact(array)
_.compact([0, 1, false, 2, '', 3]); // Creates an array with all falsey values removed

_.concat(array, [values])
var other = _.concat(array, 2, [3], [[4]]);

_.difference(array, [values])
_.difference([3, 2, 1], [4, 2]); // → [3, 1]

_.flatten(array) // Flattens array a single level deep
_.flatten([1, [2, [3, [4]], 5]]); // → [1, 2, [3, [4]], 5]

_.join(array, [separator=',']) // Converts all elements in array into a string separated by separator.
_.join(['a', 'b', 'c'], '~'); // → 'a~b~c'

_.last(array) // Gets the last element of array.

_.reverse() // This method mutates array and is based on Array#reverse.

_.slice(array, [start=0], [end=array.length])

_.sortedUniq(array) // like _.uniq except that it’s designed and optimized for sorted arrays.

_.union([arrays]) // Creates an array of unique values, in order, from all given arrays using SameValueZero for equality comparisons.
_.union([2, 1], [4, 2], [1, 2]); // → [2, 1, 4]

_.uniq(array) // Creates a duplicate-free version of an array, using SameValueZero for equality comparisons, in which only the first occurrence of each element is kept.

_.zip([arrays]) // Creates an array of grouped elements, the first of which contains the first elements of the given arrays, the second of which contains the second elements of the given arrays, and so on.
_.zip(['fred', 'barney'], [30, 40], [true, false]); // → [['fred', 30, true], ['barney', 40, false]]
```
