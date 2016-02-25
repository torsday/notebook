# CoffeeScript

*From: [Wikipedia](https://en.wikipedia.org/wiki/CoffeeScript)*

> A programming language that transcompiles to JavaScript. It adds syntactic sugar inspired by Ruby, Python and Haskell in an effort to enhance JavaScript's brevity and readability. Specific additional features include list comprehension and pattern matching.

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

-   [CoffeeScript.org](http://coffeescript.org/)
-   [Wikipedia: CoffeeScript](https://en.wikipedia.org/wiki/CoffeeScript)]
