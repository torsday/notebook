# Gearman

*From: [GearmanHQ](http://gearmanhq.com/help/getting-started)*

> A generic application framework for doing work in the background, spanning different machines, networks, and workers, each suited to preforming a specific job or set of jobs. Gearman itself acts as the central nervous system: jobs can come in from a variety of source, and workers can be on several machines and running in several different langauges.

Gearman has three main actors: clients who , the managers (servers) that are , and then handing those jobs out to workers that ultimately complete the tasks.

![Gearman Flowchart](https://upload.wikimedia.org/wikipedia/en/c/c5/Gearman_Stack.png)

---

## Definitions

### Worker

The thing that ultimately completes the tasks.

### Client

Request that work be completed by somebody.

### Manager (Server)

Responsible for accepting jobs from clients, then handing those jobs out to workers.

### Workload

The serializable object passed back and forth.

---

## References

-   <http://gearman.org/getting-started/>
-   [Jay Paroline: How Grooveshark Uses Gearman](http://wanderr.com/jay/how-grooveshark-uses-gearman/2011/03/27)
