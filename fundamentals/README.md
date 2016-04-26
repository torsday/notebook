# Fundamentals

---

## To Digest

### Stack Trace

*From: [Wikipedia](https://en.wikipedia.org/wiki/Stack_trace)*

> In computing, a stack trace (also called stack backtrace or stack traceback) is a report of the active stack frames at a certain point in time during the execution of a program. When a program is run, memory is often dynamically allocated in two places; the stack and the heap. Memory is contiguously allocated on a stack but not on a heap, thus reflective of their names. Stack also refers to a programming construct, thus to differentiate it, this stack is referred as the program's runtime stack. Technically, once a block of memory has been allocated on the stack, it cannot be easily removed as there can be other blocks of memory that were allocated before it. Each time a function is called in a program, a block of memory is allocated on top of the runtime stack called the activation record. At a high level, an activation record allocates memory for the function's parameters and local variables declared in the function.

> Programmers commonly use stack tracing during interactive and post-mortem debugging. End-users may see a stack trace displayed as part of an error message, which the user can then report to a programmer.

> A stack trace allows tracking the sequence of nested functions called - up to the point where the stack trace is generated. In a post-mortem scenario this extends up to the function where the failure occurred (but was not necessarily caused). Sibling function calls do not appear in a stack trace.

### Stack vs Heap

*From: [StackOverflow](http://stackoverflow.com/questions/79923/what-and-where-are-the-stack-and-heap)*

> The stack is always reserved in a LIFO (last in first out) order; the most recently reserved block is always the next block to be freed. This makes it really simple to keep track of the stack; freeing a block from the stack is nothing more than adjusting one pointer. The heap is memory set aside for dynamic allocation.Sep 17, 2008

![stack vs heap](http://i.stack.imgur.com/i6k0Z.png)
