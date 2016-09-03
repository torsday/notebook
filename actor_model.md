# Actor Model

*From: [Wikipedia](https://en.wikipedia.org/wiki/Actor_model)*

> A mathematical model of concurrent computation that treats "actors" as the universal primitives of concurrent computation.

In response to a message that it receives, an actor can:

* make local decisions
* create more actors
* send more messages
* determine how to respond to the next message received

Actors may modify private state, but **can only affect each other through messages** (avoiding the need for any locks).

---

## See Also

* [Scala](./languages/scala.md)
