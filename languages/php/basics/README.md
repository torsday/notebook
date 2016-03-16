# PHP Basics

---

**Table of Contents**

<!--lint disable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Hello World](#hello-world)
- [Variables](#variables)
- [Strings](#strings)
- [Numbers](#numbers)
- [Arrays](#arrays)
- [Control Flow](#control-flow)
- [Loops](#loops)
- [Functions](#functions)
- [Classes & Objects](#classes-objects)
- [Method & Property Visibility](#method-property-visibility)
- [Inheritance](#inheritance)
- [Class Abstraction](#class-abstraction)
- [Interfaces](#interfaces)
- [Traits](#traits)
- [References](#references)

<!-- /TOC -->

<!--lint enable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

---

---

## Hello World

```php
echo "Prints to screen";

echo "<p>PHP will parse HTML tags</p>";

print "This prints, too";

// This is a comment
```

---

## Variables

```php
$myName = "Carleton John";
```

---

## Strings

```php
echo "Concatenate" . " " . "with a dot";

echo "Let's interpolate a {$variable}";

strlen("hello")  # =>  5

substr("hello", 0, 4)  # =>  "hell"

strtoupper("hi")  # =>  "HI"

strtolower("HI")  # =>  "hi"

strpos("John", "o")  # =>  1
```

---

## Numbers

```php
round(3.145)  # =>  3
round(3.145, 1)  # =>  3.1

rand()  # =>  prints random number between 0 and 32767
rand(1, 10)  # =>  prints a random number between 0 and 10
```

---

## Control Flow

```php
>
<
>=
<=
==
!=
```

```php
if (condition) {

}
elseif (condition) {

}
else {

}
```

```php
switch(value) {
  case 0:
    echo "The value is 0";
    break;
  case 1:
    echo "The value is 1";
    break;
  case 3: // falling through
  case 4:
  case 5:
   echo "The value is between 3 and 5";
   break;
  default:
    echo "The value is neither 0 nor 1";
}
```

---

## Loops

```php
for ($i=0; $i < 10; $i++) {
  echo $i;
}
```

```php
$fruits = array("apple", "banana", "orange");

foreach ($fruits as $fruit) {
  echo $fruit;
}
```

```php
while (condition) {
  // do some stuff
}
```

```php
do {
  // This will run at once before testing the conditon
} while (condition)
```

---

## Functions

```php
function name(parameters) {
  // do stuff
  return something;
}
```

---

## Classes & Objects

```php
class Person {

  // properties:

  public $firstName;
  public $lastName;
  public $age;

  // constructor:

  public function __construct($firstName, $lastName, $age) {
    $this->firstName = $firstName;
    $this->lastName  = $lastName;
    $this->age       = $age;
  }

  // methods:

  public function greet() {
    echo "Hello, my name is {$this->firstName}!";
  }
}

$me = new Person("John", "Olmsted", 28);

echo $me->firstName  =>  "John"
```

---

## Method & Property Visibility

-   **Public** – accessible everywhere.
-   **Protected** – accessible within the class itself and subclasses.
-   **Private** – accessible only within the class itself.

---

## Inheritance

```php
class Fireman extends Person {

  // overriding an inherited method:
  public function greet() {
    echo "GET OUT OF HERE THERE'S A FIRE";
  }

}
```

---

## Class Abstraction

Abstract classes and methods may not be instantiated, and serve only to define a set of properties and methods all subclasses share. All methods marked as "abstract" must be defined by subclasses.

```php
abstract class Animal {
  abstract public function eat();
}

class Monkey extends Animal {
  public function eat() {
    echo "The Monkey munches on a banana.";
  }
}
```

---

## Interfaces

Specifies what methods a class must implement (an interface). An interface is slightly more abstract than an abstract class, because it does not imply an 'is a' relationship with classes that inherit it.

```php
interface Speech {
  public function greet($greeting);
}

class Spaniard implements Speech {

  public function greet($greeting) {
    if ($this->canUnderstand($greeting)) {
      echo "Hola, amigo!";
    }
    else {
      echo "No comprendo.";
    }
  }

}

```

---

## Traits

Sets of methods that are not inherited, but composed into classes.

There is precedence order for methods within a class. **Methods defined in the current class override trait methods**, while **trait methods override inherited methods**.

```php
trait neatBehaviors {
  public function doSomethingCool() { /* something */ }
  public function moreNeatStuff() { /* another thing */ }
}

class User {
  use neatBehaviors;
}
```

You can include multiple traits by separating them with commas:

```php
class User {
  use neatBehaviors, badBehaviors, shenanagins;
}
```

---

## References

-   [codeguy/php-the-right-way](https://github.com/codeguy/php-the-right-way)
