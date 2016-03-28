# Gearman

*From: [GearmanHQ](http://gearmanhq.com/help/getting-started)*

> A generic application framework for doing work in the background, spanning different machines, networks, and workers, each suited to preforming a specific job or set of jobs. Gearman itself acts as the central nervous system: jobs can come in from a variety of source, and workers can be on several machines and running in several different langauges.

*From: [Wikipedia](https://en.wikipedia.org/wiki/Gearman)*

> Gearman is an open source application framework designed to distribute appropriate computer tasks to multiple computers, so large tasks can be done more quickly. In some cases, load balancing rather than raw speed may be the main goal; a Web server, for instance, could use Gearman to send tasks for which it is not optimized to another computer (which may be running on a different architecture, using another operating system, or loaded with a computer language better suited to a particular operation).

---

## How it works:

> Gearman assigns each involved computer a role as **client**, **job server**, or **worker**. A worker machine can be assigned multiple instances of the worker role, which allows more powerful computers to complete more portions of a given task. Tasks originate on a client, are transmitted from the client to the job server, and performed on one or more workers. The completed task's output is then returned, again by way of the job server, to the client where the task originated. Gearman is conceptually related to MapReduce; Gearman handles MapReduce by allowing worker nodes to map out work to other workers, with the original worker acting as the reducer.

> Gearman performs coalescence on the work sent by a client. If two or more clients ask for work to be completed on the same body of work, either by seeing that the same blocks are being sent or by using the unique value sent by the client, it will coalesce the work so that only one worker is used. It does this specifically to avoid thundering herd problems which are common to cache hit failures.

> To mitigate the damage that would be done if a job server (or its network connection) were to fail, clients can be configured with more than one assigned job server; if the first assigned job server fails, another can be transparently substituted.

> Gearman implements a protocol that consists of binary packets containing requests and responses; this protocol defines the structure of messages passing between the three parts of a Gearman implementation. By default, the Gearman protocol uses TCP port 4730. It previously operated on port 7003, but this conflicted with the AFS port range and the new port (4730) was assigned by IANA.

> The name "Gearman" was chosen as an anagram for "Manager", "since it dispatches jobs to be done, but does not do anything useful itself."

![Gearman Flowchart](https://upload.wikimedia.org/wikipedia/en/c/c5/Gearman_Stack.png)

---

## References

-   [Jay Paroline: How Grooveshark Uses Gearman](http://wanderr.com/jay/how-grooveshark-uses-gearman/2011/03/27)
-   [Wikipedia: MapReduce](https://en.wikipedia.org/wiki/MapReduce)
