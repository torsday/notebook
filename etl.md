# ETL (Extract, Transform and Load)

*From: [datawarehouse4u.info](http://datawarehouse4u.info/ETL-process.html)*

> a process in data warehousing responsible for pulling data out of the source systems and placing it into a data warehouse.

---

## Basics

### Extracting

Extracting the data from source systems (SAP, ERP, other oprational systems), data from different source systems is converted into one consolidated data warehouse format which is ready for transformation processing.

### Transforming

Transforming the data may involve the following tasks:

  * applying business rules (so-called derivations, e.g., calculating new measures and dimensions),
  * cleaning (e.g., mapping NULL to 0 or "Male" to "M" and "Female" to "F" etc.),
  * filtering (e.g., selecting only certain columns to load),
  * splitting a column into multiple columns and vice versa,
  * joining together data from multiple sources (e.g., lookup, merge),
  * transposing rows and columns,
  * applying any kind of simple or complex data validation (e.g., if the first 3 columns in a row are empty then reject the row from processing)

### Loading

Loading the data into a data warehouse or data repository other reporting applications
