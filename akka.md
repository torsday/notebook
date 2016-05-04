# Akka

–   a toolkit and runtime for developing concurrent, distributed, message-based applications.

  –   _not_ a framework, more properly a library.

–   Akka provides:

    1.  Actors

    –   Asynchronous, non-blocking, message-driven model
    –   Actors form hierarchies, with parent actors (supervisors) delegating some tasks to child actors.
    –   "The quintessential feature of actor systems is that tasks are split up and delegated until they
      become small enough to be handled in one piece."

    2.  Fault Tolerance

    –   'let-it-crash' philosophy
    –   Systems are self-healing
