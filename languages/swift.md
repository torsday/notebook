# Swift

---

**Table of Contents**

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Basics](#basics)
	- [Declaration](#declaration)
	- [Type Inference](#type-inference)
	- [Data Types](#data-types)
- [Topics](#topics)
	- [Strong vs. Weak Reference](#strong-vs-weak-reference)
	- [Struc vs. Class](#struc-vs-class)
- [References](#references)

<!-- /TOC -->

---


## Basics

### Declaration

Use `let` to make a constant and `var` to make a variable.

```swift
var myVariable = 42
myVariable     = 50
let myConstant = 42
```


### Type Inference

implicit and explicit

```swift
let implicitInteger        = 70
let implicitDouble         = 70.0
let explicitDouble: Double = 70
```

### Data Types

* **Int or UInt** - This is is used for whole numbers. More specifically you can use Int32, Int64 to define 32 or 64 bit signed integer where as UInt32 or UInt64 to define 32 or 64 bit unsigned integer variables. For example, 42 and -23.
* **Float** - This is used to represent a 32-bit floating-point number and used for numbers with smaller decimal points. For example 3.14159, 0.1, and -273.158.
* **Double** - This is used to represent a 64-bit floating-point number and used when floating-point values must be very large. For example 3.14159, 0.1, and -273.158.
* **Bool** - This represents a boolean value which is either true or false.
* **String** - This is ordered collection of characters. For example, "Hello, World!"
* **Character** - This is a single-character string literal. For example, "C"
* **Optional** - This represents a variable that can hold either a value or no value.

---

## Topics

### Strong vs. Weak Reference


### Struc vs. Class


---

## References

* [iOS Dev Lib: A Swift Tour](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/GuidedTour.html)
