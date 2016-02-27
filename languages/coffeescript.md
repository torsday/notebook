# CoffeeScript

A programming language that transcompiles to JavaScript.

Inspired by Ruby, Python and Haskell in the name of brevity and readability.

Specific additional features include list comprehension and pattern matching.

## Installation

```sh
npm install -g coffee-script
```

## Basics

```coffeescript
# Assignment:
number   = 42
opposite = true
```

### Conditions:

```coffeescript
number = -42 if opposite
```

### Functions:

```coffeescript
square = (x) -> x * x
```

### Arrays:

```coffeescript
list = [1, 2, 3, 4, 5]
```

### Objects:

```coffeescript
math =
  root:   Math.sqrt
  square: square
  cube:   (x) -> x * square x
```

### Splats:

```coffeescript
race = (winner, runners...) ->
  print winner, runners
```

### Existence:

```coffeescript
alert "I knew it!" if elvis?
```

### Array comprehensions:

```coffeescript
cubes = (math.cube num for num in list)
```

## Functions

```coffeescript
square = (x) -> x * x
cube   = (x) -> square(x) * x
```

vs JS

```js
var cube, square;

square = function(x) {
  return x * x;
};

cube = function(x) {
  return square(x) * x;
};
```

### Default Values

```coffeescript
fill = (container, liquid = "coffee") ->
  "Filling the #{container} with #{liquid}..."
```

## Examples

```coffeescript
MyPackageView = require './my-package-view'

module.exports =
  myPackageView: null

  activate: (state) ->
    @myPackageView = new MyPackageView(state.myPackageViewState)

  deactivate: ->
    @myPackageView.destroy()

  serialize: ->
    myPackageViewState: @myPackageView.serialize()
```

## References

-   [CoffeeScript.org](http://coffeescript.org)
-   [Wikipedia: CoffeeScript](https://en.wikipedia.org/wiki/CoffeeScript)]
