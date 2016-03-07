# Throw vs. Raise

*From: [hasno.info](http://hasno.info/ruby-gotchas-and-caveats)*

> `catch`/`throw` are not the same as `raise`/`rescue`. `catch`/`throw` allows you to quickly exit blocks back to a point where a catch is defined for a specific symbol, raise rescue is the real exception handling stuff involving the Exception object.

-   `raise`, `fail`, `rescue`, and ensure handle **errors**, a.k.a. **exceptions**
-   `throw` and `catch` are **control flow**

*From: [Grimm, Avdi. "Throw, Catch, Raise, Rescue… I’m so Confused!"](http://rubylearning.com/blog/2011/07/12/throw-catch-raise-rescue-im-so-confused)*

> Unlike in other languages, Ruby’s throw and catch are not used for exceptions. Instead, they provide a way to terminate execution early when no further work is needed. (Grimm, 2011)

Terminating a single level of control flow, like a `while` loop, can be done with a simple `return`. Terminating many levels of control flow, like a nested loop, can be done with `throw`.

*From: [Thomas, Dave, and Andrew Hunt. "Programming Ruby."](http://ruby-doc.com/docs/ProgrammingRuby/html/tut_exceptions.html)*

> While the exception mechanism of raise and rescue is great for abandoning execution when things go wrong, it's sometimes nice to be able to jump out of some deeply nested construct during normal processing. This is where catch and throw come in handy. (Thomas and Hunt, 2001)

---

## References

-   [Grimm, Avdi. "Throw, Catch, Raise, Rescue… I’m so Confused!" RubyLearning Blog. N.p., 11 July 2011. Web. 1 Jan. 2012.](http://rubylearning.com/blog/2011/07/12/throw-catch-raise-rescue-im-so-confused)
-   [hasno.info: ruby gotchas and caveats](http://hasno.info/ruby-gotchas-and-caveats)
-   [StackOverflow: What is the difference between Raising Exceptions vs Throwing Exceptions in Ruby?](http://stackoverflow.com/questions/51021/what-is-the-difference-between-raising-exceptions-vs-throwing-exceptions-in-ruby)
-   [Thomas, Dave, and Andrew Hunt. "Programming Ruby." : The Pragmatic Programmer's Guide. N.p., 2001. Web. 29 Sept. 2015.](http://ruby-doc.com/docs/ProgrammingRuby/html/tut_exceptions.html)
