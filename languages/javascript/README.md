# Javascript

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Interactive](#interactive)
- [Some String Methods](#some-string-methods)
- [Some Math Tools](#some-math-tools)
- [Comparison Operators](#comparison-operators)
- [Conditional Statements](#conditional-statements)
- [for, While, Do While Loops](#for-while-do-while-loops)
- [for / in Loop – Used for Iterating Through Hashes or Arrays (kind of Like Ruby's .each)](#for-in-loop-used-for-iterating-through-hashes-or-arrays-kind-of-like-rubys-each)
- [Switch](#switch)
- [Arrays](#arrays)
- [Objects](#objects)
- [Constructors/“classes” or Prototypes](#constructorsclasses-or-prototypes)
- [Prototypical Inheritance:](#prototypical-inheritance)
- [Functions & Methods – a Method Is a Function Associated with an Object.](#functions-methods-a-method-is-a-function-associated-with-an-object)
- [Module Design Pattern](#module-design-pattern)
- [Hoisting](#hoisting)

<!-- /TOC -->

## Interactive

```js
confirm("Are you sure?")		throws a confirmation box at the user
prompt("Enter your name.")		prompts the user for input

console.log(//some stuff)		logs content in the console
```

## Some String Methods

```js
"String".length

.substring(x, y)			chops string between x, y exclusively (0 is start)

.toUpperCase()
.toLowerCase()

"Hello there ".concat(name)		“Hello there John”

"ruby is cool".match('cool')		["cool"]
```


## Some Math Tools

```js
Math.random()				generates a random float between 0 and 1
Math.floor()          			rounds a float
Math.floor(Math.random() * 5 + 1)       e.g. generates a random number between 1 and 5
isNaN(n);    				checks if "n" is not a number

num.toString();
```

## Comparison Operators

```js
>
<
>=
===
!==
```

## Ternary Operator

```js
condition ? expr1 : expr2
```

*[Mozilla Doc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)*


```js
var elvisLives = Math.PI > 4 ? "Yep" : "Nope";
```


## Conditional Statements

```js
if (boolean)
{

}
else if (boolean)
{

}
else
{

}
```

## for, While, Do While Loops

```js
for (var i = 1; i < 11; i++) {
	console.log(i);
}

// Use a for loop to iterate over an array
for (var i = 0; i < cities.length; i++) {
    console.log("I would like to visit " + cities[i]);
}

while (condition) {
  Do something;
}

do {
    // Do something at least once before checking the condition;
} while (condition)
```


## for / in Loop – Used for Iterating Through Hashes or Arrays (kind of Like Ruby's .each)

```js
for (var x in object) {
   // do something to x, i.e. the property in the object
   console.log(object[x]) //prints the value of the property
}
```


## Switch

```js
switch (expression) {
  case 'option1':
    since expression is option1 I'll do this;
    break;
  case 'option2':
    since expression is option2 I'll do this;
    break;
  case 'option3':
    since expression is option3 I'll do this;
    break;
  default:
    no match so I'll do this;
}
```

## Arrays

```js
Array.length
e
Array.push(item)		Adds item to the array.
Array.pop()

Array.unshift(item)
Array.shift

Array.first()
Array.last()

Array.indexOf(object)
Array.indexOf(object) > -1	Janky implementation of Ruby’s .include?

Array.join()
String.split()

array1.concat(array2)
```


## Objects

```js
var myObject = {		literal notation.
    key: value,			in Javascript key-value pairs are called "properties"
    key: value,
    key: value,
    method: function() {
      do something;
    }
};
```

or

```js
var myObject = new Object();		constructor notation
myObject["key"] = "value";

myObject.key;				accessing and editing properties
or
myObject["key"]

delete myObject.key			delete a property

typeof variable   			returns what type of object a variable is
object.hasOwnProperty(parameter)  	determines whether an object has a given property
```


## Constructors/“classes” or Prototypes

```js
var Thing = function(parameter1, parameter2) {
  // Without the ‘this’ prefix, this is not a public property but a local variable.
  var exists = true;

  this.parameter1 = parameter1;
  this.parameter2 = parameter2;
  this.constant   = "The same for all instances."

  this.method = function() {
    do something;
  }

  // Writer for the local variable ‘exists’
  this.exists = function(boolean) {
    fullName = boolean;
  };
};

var ball = new thing("round", "red");

// OR

var ball = thing.new(“round”, “red”);


// Adding a method to a class (but why wouldn't you include this in the constructor..?)
className.prototype.newMethod = function() {
do some stuff;
};


// How to make a constructor inherit from another. This is PROTOTYPICAL inheritance, not
// CLASS inheritance.
Child.prototype = new Parent();


// Another example of prototypical inheritance:

var Flower = function(family) {
  var family     = family;
  this.kingdom   = 'Plantae';
  this.division  = 'Angiospermae';
  this.getFamily = function() { return family };
};

var Orchid = function(name, isEpiphyte) {
  var name        = name;
  this.isEpiphyte = isEpiphyte;
  this.getName    = function() { return name };
};

Orchid.prototype = new Flower("Orchidaceae");
```


## Prototypical Inheritance:

By assigning an instance of Flower to the prototype for Orchid, we have determined
that any instances of Orchid will inherit the properties and methods of Flower.

When accessing a property or calling a method on an object, JavaScript looks up the prototype chain. In other words, if the property or method is not defined by the object itself, JavaScript looks for it within the object constructor. Then, if the property or method is not defined, JavaScript will look for it in the prototype object, and will keep looking all the way up the chain until it finds it. This, like classical inheritance, is a form of automatic message delegation.


## Functions & Methods – a Method Is a Function Associated with an Object.

```js
var functionName = function(parameter) {
  some stuff to do;
  return something;
};
```

or

```js
function functionName(parameter) {
  some stuff to do;
  return somethin;
};
```


```this``` keyword allows a function to act like a method for any object, where "this" stands in for the object name. The function is then assigned to the object.

```js
var universalMethod = function(parameter) {
  this.key = parameter;
};

object.universalMethod = universalMethod;
```


## Module Design Pattern

Useful for creating objects with public/private interfaces.

```js
var Speaker = (function() {
  var thisIsPrivate = “Hello my friend”;

  return {
    speak: function() {
      console.log(thisIsPrivate);
    }
  }
}())

Speaker.thisIsPrivate => undefined!
Speaker.speak => “Hello my friend”
```

In this sense Speaker is a closure, because it encapsulates the scope of whole function.


## Hoisting

Can result in confusing scope issues. As a rule,

"Function declarations and function variables are always moved ('hoisted') to the top of their javascript code by the interpreter."
[http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html]

NOTE that this means that while variable declarations are hoisted, their assignments are not!

```js
function hoistMe() {
  // logs 'undefined' – `variable` is hoisted, but has not assignment value.
  console.log(variable);
  var variable = "hello";
}

Function _declarations_ are hoisted along with their function bodies. This returns 'blerg', because the second definition of stuff() is hoisted above the return statement:

function returnStuff() {
  function stuff() {
    return "blah";
  }
  return stuff();
  function stuff() {
    return "blerg";
  }
}
```

By contrast, function _expressions_ hoist their variable declarations, but NOT their assignment expressions – i.e., their function bodies. Therefor the following example returns 'blah', because the second function body of stuff() is not hoisted, and is declared after the 'return' statement:

```js
function returnStuff() {
  var stuff = function() {
    return "blah";
  }
  return stuff();
  var stuff = function() {
    return "blerg";
  }
}
```


# Callbacks

1. Callbacks are functions that are executed asynchronously.

1. Instead of executing top to bottom ('procedurally') like synchronous code, asynchronous code executes different functions are different times based on the order and speed that earlier functions are executed.

1. This can lead to serious confusion if we think 'procedurally' when we write our code. For example, consider this bit of javascript that parses a number stored in a file using node:

    ```js
    var fs = require('fs');
    var myNumber = undefined;

    function addOne() {
      fs.readFile('number.txt', function doneReading(err, fileContents) {
        myNumber = parseInt(fileContents);
      })
    }

    addOne();

    console.log(myNumber); // logs out undefined
    ```

1. When we run this code, 'myNumber' is undefined, because console.log() has executed before readfile() was done executing. It is NOT running procedurally, waiting for one line to finish before moving on to the next. We can solve this problem with a callback. The callback doesn't know WHEN it will execute, but it knows WHERE it will execute, i.e. in what order relative to other functions

    ```js
    var fs = require('fs');
    var myNumber = undefined;

    function addOne(callback) {
      fs.readFile('number.txt', function doneReading(err, fileContents) {
        myNumber = parseInt(fileContents);
        callback(); // we know this callback will execute AFTER readFile()
      })
    }

    function logMyNumber() { // defining the callback we'll use
      console.log(myNumber);
    }

    addOne(logMyNumber); // logs out '1000', or whatever 'number.txt' contains
    ```

1. Since the crux of node is asynchronous I/O, almost every node function takes a callback. Here is a typical example:

    ```js
    var fs = require('fs')

    function finishedReading(error, fileData) {
      if (error) throw error
      // do something with the fileData
    }

    fs.readFile('movie.mp4', finishedReading)
    ```


## References

* [DrkSephy/es6-cheatsheet](https://github.com/DrkSephy/es6-cheatsheet)
