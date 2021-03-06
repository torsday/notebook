# Publish–subscribe pattern

*From: [Wikipedia](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern)*

> In software architecture, publish–subscribe is a messaging pattern where senders of messages, called publishers, do not program the messages to be sent directly to specific receivers, called subscribers, but instead characterize published messages into classes without knowledge of which subscribers, if any, there may be. Similarly, subscribers express interest in one or more classes and only receive messages that are of interest, without knowledge of which publishers, if any, there are.

> Pub/sub is a sibling of the message queue paradigm, and is typically one part of a larger message-oriented middleware system. Most messaging systems support both the pub/sub and message queue models in their API, e.g. Java Message Service (JMS).

> This pattern provides greater network scalability and a more dynamic network topology, with a resulting decreased flexibility to modify the Publisher and its structure of the data published.
