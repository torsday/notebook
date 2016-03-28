# Gearman

An open source application framework designed to distribute computer tasks to multiple computers, in the interest of speed and/or load balancing.

*From: [GearmanHQ](http://gearmanhq.com/help/getting-started)*

> A generic application framework for doing work in the background, spanning different machines, networks, and workers, each suited to preforming a specific job or set of jobs. Gearman itself acts as the CNS: jobs can come in from a variety of source, and workers can be on several machines and running in several different langauges.

An anagram for *Manager*, "since it dispatches jobs to be done, but does not do anything useful itself."

---

## How it works:

Gearman assigns each involved computer a role as **client**, **job server**, or **worker**. Tasks originate on a client, are transmitted from the client to the job server, and performed on one or more workers. The completed task's output is then returned, again by way of the job server, to the client where the task originated.

Conceptually related to MapReduce; Gearman handles MapReduce by allowing worker nodes to map out work to other workers, with the original worker acting as the reducer.

Gearman performs coalescence on the work sent by a client. If two or more clients ask for work to be completed on the same body of work, either by seeing that the same blocks are being sent or by using the unique value sent by the client, it will coalesce the work so that only one worker is used. It does this specifically to avoid thundering herd problems which are common to cache hit failures.

### Worker

-   A worker machine can be assigned multiple instances of the worker role, which allows more powerful computers to complete more portions of a given task.

### Clients

-   To mitigate the damage that would be done if a job server (or its network connection) were to fail, clients can be configured with more than one assigned job server; if the first assigned job server fails, another can be transparently substituted.

![Gearman Flowchart](https://upload.wikimedia.org/wikipedia/en/c/c5/Gearman_Stack.png)

---

## References

-   [Jay Paroline: How Grooveshark Uses Gearman](http://wanderr.com/jay/how-grooveshark-uses-gearman/2011/03/27)
-   [Wikipedia: Gearman](https://en.wikipedia.org/wiki/Gearman)
-   [Wikipedia: MapReduce](https://en.wikipedia.org/wiki/MapReduce)
