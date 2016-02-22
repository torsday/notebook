# Lightweight Directory Access Protocol *(LDAP)*

*From: [Zytrax](http://www.zytrax.com/books/ldap/ch2/index.html#history)*
> A protocol that defines the method by which directory data is accessed. Necessarily, it also defines and describes how data is represented in the directory service (the Data (Information) Model). Finally, it defines how data is loaded (imported) into and saved (exported) from a directory service (using LDIF). LDAP does not define how data is stored or manipulated. Data storage and access methods are automagical processes as far as the standard is concerned and are generally handled by back-end modules (typically using some form of transaction database) within any specific LDAP implementation.

* A directory service protocol.
* Runs on a layer above the TCP/IP stack.
* Provides a mechanism for CRUD operations on internet directories.
* Based on a client-server model.

---

**Table of Contents**

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Why?](#why)
- [Basics](#basics)
	- [Permissions](#permissions)
	- [Schema](#schema)
		- [Example](#example)
- [Setting up an LDAP Server](#setting-up-an-ldap-server)
- [LDAP Data Interchange Format *(LDIF)*](#ldap-data-interchange-format-ldif)
	- [Fields](#fields)
	- [Examples](#examples)
- [See Also](#see-also)
- [References](#references)

<!-- /TOC -->

---

## Why?

* System administrators have embraced LDAP because it offers them a way to centralize and make available all sorts of infrastructure information.
* Industry standard for directory access.

## Basics

* Connecting with authentication is the usual first step in any LDAP client/server transaction. In LDAP-speak this is known as “binding to the server.”

### Permissions

Set by the administrator to allow only certain people to access the LDAP database, and optionally keep certain data private.

### Schema

A way to describe the format and attributes of data in the server. For example: a schema entered in an LDAP server might define a `groovyPerson` entry type, which has attributes of `instantMessageAddress`, and `coffeeRoastPreference`. The normal attributes of `name`, `email` `address`, etc., would be inherited from one of the standard schemas, which are rooted in X.500.

#### Example

*source: [O'Reilly: LDAP Tutorial][oreilly-tutorial]*

```sh
residentialPerson
   ( 2.5.6.10 NAME 'residentialPerson' SUP person STRUCTURAL MUST l
     MAY ( businessCategory $ x121Address $ registeredAddress $
     destinationIndicator $ preferredDeliveryMethod $ telexNumber $
     teletexTerminalIdentifier $ telephoneNumber $
     internationaliSDNNumber $
     facsimileTelephoneNumber $ preferredDeliveryMethod $ street $
     postOfficeBox $ postalCode $ postalAddress $
     physicalDeliveryOfficeName $ st $ l ) )
```

This definition says that an entry of object class `residentialPerson` must have a `l` attribute (short for locality) and may have a whole other set of attributes (`registeredAddress`, `postOfficeBox`, etc.). The key part of the specification is the `SUP` person string. It says that the superior class (the one from which `residentialPerson` inherits its attributes) is the `person` object class. That class’s definition looks like this:

```sh
person
   ( 2.5.6.6 NAME 'person' SUP top STRUCTURAL MUST ( sn $ cn )
     MAY ( userPassword $ telephoneNumber $ seeAlso $ description ) )
```

So, an entry with object class of `residentialPerson` must have `sn` (surname), `cn` (common name), and `l` (locality) attributes and may have the other attributes listed in the `MAY` sections of these two RFC excerpts. We also know that person is the top of the object hierarchy for `residentialPerson`, since its superior class is the special abstract class top.

In most cases, you can get away with using the predefined standard object classes. If you need to construct entries with attributes not found in an existing object class, it is usually good form to locate the closest existing object class and build upon it, like `residentialPerson` builds upon person.






## Setting up an LDAP Server


## LDAP Data Interchange Format *(LDIF)*

A standard plain text data interchange format for representing LDAP directory CRUD requests.

1. Conveys directory content as a set of records, one record for each object (or entry).
1. Represents update requests, such as Add, Modify, Delete, and Rename, as a set of records, one record for each update request.


### Fields

- `dn`: **Distinguished Name**
    - This refers to the name that uniquely identifies an entry in the directory.
    - DNs have a “most specific component first” ordering, like postal addresses.
- `dc`: **Domain Component**
    - This refers to each component of the domain. For example `www.google.com` would be written as `DC=www,DC=google,DC=com`
- `ou`: **Organizational Unit**
    - This refers to the organizational unit (or sometimes the user group) that the user is part of. If the user is part of more than one group, you may specify as such, e.g., `OU= Lawyer,OU= Judge`.
- `cn`: **Common Name**
    - This refers to the individual object (person's name; meeting room; recipe name; job title; etc.) for whom/which you are querying.


### Examples

Directory entry with several attributes, represented as a record.

```sh
dn: cn=The Postmaster,dc=example,dc=com
objectClass: organizationalRole
cn: The Postmaster
```

Modify multiple single-valued attributes for two different directory entries.

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

Note:
- the `-` character between each attribute change is required.
- each directory entry ends with a `-` followed by a blank line.
- The final `-` is required.

Add a telephone number to an existing user.

```sh
dn: cn=Peter Michaels, ou=Artists, l=San Francisco, c=US
changetype: modify
add: telephonenumber
telephonenumber: +1 415 555 0002
```

## See Also

* [self: directory](../persistence/README.md#Directory-vs-Database)


## References

* [CentOS: LDIF Update Statements](https://www.centos.org/docs/5/html/CDS/ag/8.0/Creating_Directory_Entries-LDIF_Update_Statements.html)
* [Microsoft](https://msdn.microsoft.com/en-us/library/windows/desktop/aa367008)
* [O'Reilly: LDAP Tutorial][oreilly-tutorial]
* [OpenLDAP Setup Overview](https://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-ldap-quickstart.html)
* [TLDP: LDAP, How To](http://www.tldp.org/HOWTO/LDAP-HOWTO/index.html)
* [Wikipedia: LDAP](https://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol)
* [Wikipedia: LDIF](https://en.wikipedia.org/wiki/LDAP_Data_Interchange_Format)
* [Zytrax: LDAP for Rocket Scientists](http://www.zytrax.com/books/ldap/)

[oreilly-tutorial]: http://archive.oreilly.com/pub/a/perl/excerpts/system-admin-with-perl/ten-minute-ldap-utorial.html
