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

```
