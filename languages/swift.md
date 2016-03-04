# Swift

---

**Table of Contents**

<!--lint disable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Basics](#basics)
  - [Declaration](#declaration)
  - [Type Inference](#type-inference)
  - [Data Types](#data-types)
  - [Conditionals](#conditionals)
- [Topics](#topics)
  - [Strong vs. Weak Reference](#strong-vs-weak-reference)
  - [Struc vs. Class](#struc-vs-class)
- [References](#references)

<!-- /TOC -->

<!--lint enable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

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

-   `Int` or `UInt`

    -   You can use Int32, Int64 to define 32 or 64 bit signed integer where as UInt32 or UInt64 to define 32 or 64 bit unsigned integer variables.

-   `Float`

    -   32-bit floating-point number

-   `Double`

    -   64-bit float

-   `Bool`

-   `String`

-   `Character`

-   `Optional`

    -   Can hold either a value or no value.

### Conditionals

```swift
if onSaleInferred {
  print("\(nameInferred) on sale for \(priceInferred)!")
} else {
  print("\(nameInferred) at regular price: \(priceInferred)!")
}
```

---

### Statements

#### Guard

---

## Topics

### Strong vs. Weak Reference

### Struc vs. Class

---

## References

-   [Apple: Swift Resources](https://developer.apple.com/swift/resources)
-   [iOS Dev Lib: A Swift Tour](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/GuidedTour.html)
-   [Source on GitHub](https://github.com/apple/swift)
-   [Tutorials Point: Swift](http://www.tutorialspoint.com/swift)
