# Persistence

---

## Genres

---

### Relational

This is the most common classic database pattern. Relational database management systems (RDBMSs) are set-theory-based systems implemented as two-dimensional tables with rows and columns. Relational databases strictly enforce type and are generally numeric, strings, dates, and uninterpreted blobs, but as we saw, PostgreSQL provided extensions such as array or cube.

#### Good For:

Because of the structured nature of relational databases, they make sense when the layout of the data is known in advance but how you plan to use that data later may not be. Or, in other words, you pay the organizational complexity up front to achieve query flexibility later. Many business problems are aptly modeled this way, from orders to shipments and from inventory to shopping carts. You may not know in advance how you’ll want to query the data later—how many orders did we process in February?—but the data is quite regular in nature, so enforcing that regularity is helpful.

#### Not-So-Good For:

When your data is highly variable or deeply hierarchical, relational databases aren’t the best fit. Because you must specify a schema up front, data problems that exhibit a high degree of record-to-record variation will be problematic. Consider developing a database to describe all the creatures in nature. Creating a full list of all features to account for (hasHair, numLegs, laysEggs, and so on) would be intractable. In such a case, you’d want a database that makes less restrictions in advance on what you can put into it.

---

### Key-value

The key-value (KV) store was the simplest model we covered. KV maps simple keys to (possibly) more complex values like a huge hashtable. Because of their relative simplicity, this genre of database has the most flexibility of implementation. Hash lookups are fast, so in the case of Redis, speed was its primary concern. Hash lookups are also easily distributed, and so Riak took advantage of this fact for focusing on simple-to-manage clusters. Of course, its simplicity can be a downside for any data with complex modeling requirements.

#### Good For:

With little or no need to maintain indexes, key-value stores are often designed to be horizontally scalable, extremely fast, or both. They’re particularly suited for problems where the data are not highly related. For example, in a web application, users’ session data meet this criteria; each user’s session activity will be different and largely unrelated to the activity of other users.

#### Not-So-Good For:

Often lacking indexes and scanning capabilities, KV stores won’t help you if you need to be able to perform queries on your data, other than basic CRUD operations (Create, Read, Update, Delete).

---

### Columnar

Columnar databases (aka column-oriented, aka column family) share many similarities with both KV and RDBMS stores. Like with a key-value database, values are queried by matching keys. Like relational, their values are groups of zero or more columns, though each row is capable of populating however many it wants. Unlike either, columnar databases store like data by columns, rather than keeping data together by rows. Columns are inexpensive to add, versioning is trivial, and there is no real storage cost for unpopulated values. We saw how HBase is a classic implementation of this genre.

#### Good For:

Columnar databases have been traditionally developed with horizontal scalability as a primary design goal. As such, they’re particularly suited to “Big Data” problems, living on clusters of tens, hundreds, or thousands of nodes. They also tend to have built-in support for features such as compression and versioning. The canonical example of a good columnar data storage problem is indexing web pages. Pages on the Web are highly textual (benefits from compression), somewhat interrelated, and change over time (benefits from versioning).

#### Not-So-Good For:

Different columnar databases have different features and therefore different drawbacks. But one thing they have in common is that it’s best to design your schema based on how you plan to query the data. This means you should have some idea in advance of how your data will be used, not just what it’ll consist of. If data usage patterns can’t be defined in advance—for example, fast ad hoc reporting—then a columnar database may not be the best fit.

---

### Document

Document databases allow for any number of fields per object and even allow objects to be nested to any depth as values of other fields. The common representation of these objects is as JavaScript Object Notation (JSON), adhered to by both MongoDB and CouchDB—though this is by no means a conceptual requirement. Since documents don’t relate to each other like relational databases, they are relatively easy to shard and replicate across several servers, making distributed implementations fairly common. MongoHQ tends to tackle availability by supporting the creation of datacenters that manage huge datasets for the Web. Meanwhile, CouchDB focuses on being simple and durable, where availability is achieved by master-master replication of fairly autonomous nodes. There is high overlap between these projects.

#### Good For:

Document databases are suited to problems involving highly variable domains. When you don’t know in advance what exactly your data will look like, document databases are a good bet. Also, because of the nature of documents, they often map well to object-oriented programming models. This means less impedance mismatch when moving data between the database model and application model.

#### Not-So-Good For:

If you’re used to performing elaborate join queries on highly normalized relational database schemas, you’ll find the capabilities of document databases lacking. A document should generally contain most or all of the relevant information required for normal use. So while in a relational database you’d naturally normalize your data to reduce or eliminate copies that can get out of sync, with document databases, denormalized data is the norm.

---

### Graph

Graph databases are an emerging class of database that focuses more on the free interrelation of data than the actual values. Neo4j, as our open source example, is growing in popularity for many social network applications. Unlike other database styles that group collections of like objects into common buckets, graph databases are more free-form—queries consist of following edges shared by two nodes or, namely, traversing nodes. As more projects use them, graph databases are growing the straightforward social examples to occupy more nuanced use cases, such as recommendation engines, access control lists, and geographic data.

#### Good For:

Graph databases seem to be tailor-made for networking applications. The prototypical example is a social network, where nodes represent users who have various kinds of relationships to each other. Modeling this kind of data using any of the other styles is often a tough fit, but a graph database would accept it with relish. They are also perfect matches for an object-oriented system. If you can model your data on a whiteboard, you can model it in a graph.

#### Not-So-Good For:

Because of the high degree of interconnectedness between nodes, graph databases are generally not suitable for network partitioning. Spidering the graph quickly means you can’t afford network hops to other database nodes, so graph databases don’t scale out well. It’s likely that if you use a graph database, it’ll be one piece of a larger system, with the bulk of the data stored elsewhere and only the relationships maintained in the graph.

---

## Directory vs Database

A **directory** is similar to a database, but

-   Tends to **contain more descriptive, attribute-based information**.

-   Generally **read from more often than written to**.

-   Tuned to give **quick-response to high-volume requests**.

-   They may have the **ability to replicate information widely** in order to increase availability and reliability, while reducing response time.

    -   Temporary inconsistencies between the replicas may be OK, as long as they get in sync eventually.

---

## References

-   [Redmond, "Seven Databases in Seven Weeks"](http://www.amazon.com/Seven-Databases-Weeks-Modern-Movement/dp/1934356921)
