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

A standard plain text data interchange format for representing LDAP directory CRUD requests.

1. Conveys directory content as a set of records, one record for each object (or entry).
1. Represents update requests, such as Add, Modify, Delete, and Rename, as a set of records, one record for each update request.


### Fields

- `dn`: distinguished name
    - This refers to the name that uniquely identifies an entry in the directory.
- `dc`: domain component
    - This refers to each component of the domain. For example `www.google.com` would be written as `DC=www,DC=google,DC=com`
- `ou`: organizational unit
    - This refers to the organizational unit (or sometimes the user group) that the user is part of. If the user is part of more than one group, you may specify as such, e.g., `OU= Lawyer,OU= Judge`.
- `cn`: common name
    - This refers to the individual object (person's name; meeting room; recipe name; job title; etc.) for whom/which you are querying.


### Examples

Simple directory entry with several attributes, represented as a record

```sh
dn: cn=The Postmaster,dc=example,dc=com
objectClass: organizationalRole
cn: The Postmaster
```

An LDIF record that modifies multiple single-valued attributes for two different directory entries

```sh
dn: CN=John Smith,OU=Legal,DC=example,DC=com
changetype: modify
replace:employeeID
employeeID: 1234
-
replace:employeeNumber
employeeNumber: 98722
-
replace: extensionAttribute6
extensionAttribute6: JSmith98
-

dn: CN=Jane Smith,OU=Accounting,DC=example,DC=com
changetype: modify
replace:employeeID
employeeID: 5678
-
replace:employeeNumber
employeeNumber: 76543
-
replace: extensionAttribute6
extensionAttribute6: JSmith14
-
```

*Note: the "-" character between each attribute change is required. Also note that each directory entry ends with a "-" followed by a blank line. The final "-" is required.*

An LDIF file that adds a telephone number to an existing user

```sh
dn: cn=Peter Michaels, ou=Artists, l=San Francisco, c=US
changetype: modify
add: telephonenumber
telephonenumber: +1 415 555 0002
```

## References

* [Microsoft](https://msdn.microsoft.com/en-us/library/windows/desktop/aa367008)
* [OpenLDAP Setup Overview](https://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-ldap-quickstart.html)
* [TLDP: LDAP, How To](http://www.tldp.org/HOWTO/LDAP-HOWTO/index.html)
* [Wikipedia: LDAP](https://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol)
* [Wikipedia: LDIF](https://en.wikipedia.org/wiki/LDAP_Data_Interchange_Format)
