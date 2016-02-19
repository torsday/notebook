# Lightweight Directory Access Protocol (LDAP)

## What is LDAP?

* A directory service protocol.
* Runs on a layer above the TCP/IP stack.
* Provides a mechanism for CRUD operations on internet directories.
* Based on a client-server model.

### Directory vs Database

A **directory** is similar to a database, but
- Tends to **contain more descriptive, attribute-based information**.
- Generally **read from more often than written to**.
- Tuned to give **quick-response to high-volume requests**.
- They may have the **ability to replicate information widely** in order to increase availability and reliability, while reducing response time.
    - Temporary inconsistencies between the replicas may be OK, as long as they get in sync eventually.


## Permissions

Set by the administrator to allow only certain people to access the LDAP database, and optionally keep certain data private.

## Schema

A way to describe the format and attributes of data in the server. For example: a schema entered in an LDAP server might define a "groovyPerson" entry type, which has attributes of "instantMessageAddress", and "coffeeRoastPreference". The normal attributes of name, email address, etc., would be inherited from one of the standard schemas, which are rooted in X.500.


## Setting up an LDAP Server


## LDAP Data Interchange Format (LDIF)

*From: [Wikipedia](https://en.wikipedia.org/wiki/LDAP_Data_Interchange_Format)*
> A standard plain text data interchange format for representing LDAP directory content and update requests.

> LDIF conveys directory content as a set of records, one record for each object (or entry). It also represents update requests, such as Add, Modify, Delete, and Rename, as a set of records, one record for each update request.

## References

* [Microsoft](https://msdn.microsoft.com/en-us/library/windows/desktop/aa367008)
* [OpenLDAP Setup Overview](https://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-ldap-quickstart.html)
* [TLDP: LDAP, How To](http://www.tldp.org/HOWTO/LDAP-HOWTO/index.html)
