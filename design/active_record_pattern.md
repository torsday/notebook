# Active Record Pattern

*From: [Wikipedia](https://en.wikipedia.org/wiki/Active_record_pattern)*
> An architectural pattern found in software that stores in-memory object data in relational databases.

> An approach to accessing data in a database. A database table or view is wrapped into a class. Thus, an object instance is tied to a single row in the table. After creation of an object, a new row is added to the table upon save. Any object loaded gets its information from the database. When an object is updated the corresponding row in the table is also updated. The wrapper class implements accessor methods or properties for each column in the table or view.
