# Lightweight Directory Access Protocol (LDAP)


## What is LDAP?

*From: [Microsoft](https://msdn.microsoft.com/en-us/library/windows/desktop/aa367008)*
> A directory service protocol that runs on a layer above the TCP/IP stack. It provides a mechanism used to connect to, search, and modify Internet directories. The LDAP directory service is based on a client-server model.

*From: [Gracion](http://www.gracion.com/server/whatldap.html)*
> As a protocol, LDAP does not define how programs work on either the client or server side. It defines the "language" used for client programs to talk to servers (and servers to servers, too)

### Directory?

*From: [TLDP](http://www.tldp.org/HOWTO/LDAP-HOWTO/whatisldap.html)*
> A **directory** is similar to a database, but tends to contain more descriptive, attribute-based information. The information in a directory is generally **read much more often than it is written**. Directories are tuned to give quick-response to high-volume lookup or search operations. They may have the ability to replicate information widely in order to increase availability and reliability, while reducing response time. When directory information is replicated, temporary inconsistencies between the replicas may be OK, as long as they get in sync eventually.


## LDAP defines Permissions & Schema

### Permissions

Set by the administrator to allow only certain people to access the LDAP database, and optionally keep certain data private.

### Schema

A way to describe the format and attributes of data in the server. For example: a schema entered in an LDAP server might define a "groovyPerson" entry type, which has attributes of "instantMessageAddress", and "coffeeRoastPreference". The normal attributes of name, email address, etc., would be inherited from one of the standard schemas, which are rooted in X.500.


## Setting up an LDAP Server




## References

* [OpenLDAP Setup Overview](https://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-ldap-quickstart.html)
