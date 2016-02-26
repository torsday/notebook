# Design

---

**Table of Contents**

<!--lint disable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Principles](#principles)
- [Architecture](#architecture)
- [Design Patterns](#design-patterns)
	- [Creational](#creational)
	- [Structural](#structural)
	- [Behavioral](#behavioral)
- [References](#references)

<!-- /TOC -->

<!--lint enable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

---

## Principles

-   [SOLID Principles](./solid.md)

## Architecture

-   [Domain Driven Design](./ddd.md)
-   [Onion](./onion.md)

## Design Patterns

-   [Abstract Factory](./abstract_factory.md)
-   [Active Record Pattern](./active_record_pattern.md)
-   [Adapter](./adapter.md)
-   [Bridge](./bridge.md)
-   [Chain of Responsibility](./chain_of_responsibility.md)
-   [Command](./command.md)
-   [Composite](./composite.md)
-   [CQRS](./cqrs.md)
-   [Decorator](./decorator.md)
-   [Factory Method](./factory_method.md)
-   [Flyweight](./flyweight.md)
-   [Hexagonal](./hexagonal.md)
-   [Iterator](./iterator.md)
-   [Lazy Loading](./lazy_loading.md)
-   [Mediator](./mediator.md)
-   [Memento](./memento.md)
-   [MVC](./mvc.md)
-   [Observer](./observer.md)
-   [Proxy](./proxy.md)
-   [Pub-sub Pattern](./pub_sub.md)
-   [Singleton](./singleton.md)
-   [Specification Pattern](./specification_pattern.md)
-   [State](./state.md)
-   [Strategy](./strategy.md)
-   [Template](./template.md)

### Creational

[Source Making][source_making]

> These design patterns are all about class instantiation. This pattern can be further divided into class-creation patterns and object-creational patterns. While class-creation patterns use inheritance effectively in the instantiation process, object-creation patterns use delegation effectively to get the job done.

### Structural

[Source Making][source_making]

> These design patterns are all about Class and Object composition. Structural class-creation patterns use inheritance to compose interfaces. Structural object-patterns define ways to compose objects to obtain new functionality.

### Behavioral

[Source Making][source_making]

> These design patterns are all about Class's objects communication. Behavioral patterns are those patterns that are most specifically concerned with communication between objects.

## References

-   [Source Making: Design Patterns][source_making]

[source_making]: https://sourcemaking.com/design_patterns "Source Making: Design Patterns"
